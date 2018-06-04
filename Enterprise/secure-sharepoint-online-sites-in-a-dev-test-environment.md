---
title: Защита сайтов SharePoint Online в среде разработки и тестирования
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/17/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: Сводка. Создание общедоступных, частных, конфиденциальных и строго конфиденциальных сайтов групп SharePoint Online в среде разработки и тестирования.
ms.openlocfilehash: fecb725999c7958dca1278c1236fcf251adc33cd
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193729"
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="6b6e3-103">Защита сайтов SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="6b6e3-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="6b6e3-104">**Сводка.** Создание общедоступных, частных, конфиденциальных и строго конфиденциальных сайтов групп SharePoint Online в среде разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="6b6e3-105">Эта статья содержит пошаговые инструкции по созданию среды разработки и тестирования, включающей четыре различных типа сайтов групп SharePoint Online для [решения по защите файлов и сайтов SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files solution](secure-sharepoint-online-sites-and-files.md).</span></span>
  
![Все четыре сайта группы в безопасной среде разработки и тестирования SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="6b6e3-107">Используйте это окружение разработки и тестирования для экспериментов с режимами защиты информации и настройкой перед развертыванием сайтов групп SharePoint Online в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="6b6e3-108">Этап 1. Создание среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="6b6e3-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="6b6e3-109">На этом этапе вы получите пробные подписки для Office 365 и Enterprise Mobility + Security для вымышленной организации.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="6b6e3-110">Сначала следуйте инструкциям для **этапа 2**, представленного в [разделе о среде разработки и тестирования Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="6b6e3-111">Затем оформите пробную подписку на EMS и добавьте ее к той же организации, что и пробную подписку на Office 365.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="6b6e3-p101">Если необходимо, войдите на портал Office 365 с использованием учетных данных учетной записи глобального администратора пробной подписки. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6b6e3-114">Выберите плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="6b6e3-115">Открыв вкладку **Центр администрирования Office** в браузере, на панели навигации слева щелкните **Выставление счетов > Приобретение служб**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="6b6e3-p102">На странице **Приобретение служб** найдите элемент **Enterprise Mobility + Security E5**. Наведите на него указатель мыши и выберите **Начать бесплатный пробный период**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="6b6e3-118">На странице **Подтверждение заказа** нажмите кнопку **Попробовать**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="6b6e3-119">На странице **Получение заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="6b6e3-120">Затем включите лицензию Enterprise Mobility + Security E5 для своей учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="6b6e3-121">Открыв вкладку браузера **Центр администрирования Office 365**, на панели навигации слева выберите **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="6b6e3-122">Выберите свою учетную запись глобального администратора и щелкните ссылку **Изменить** для параметра **Лицензии на продукты**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="6b6e3-123">На панели **Лицензии на продукты** переведите переключатель **Enterprise Mobility + Security E5** в положение **Вкл.**, нажмите **Сохранить**, а затем дважды **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="6b6e3-124">Этап 2. Создание и настройка групп и пользователей Azure Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="6b6e3-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="6b6e3-125">На этом этапе вы создадите и настроите группы и пользователей Azure AD для вымышленной организации.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="6b6e3-126">Сначала создайте набор групп для обычной организации на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="6b6e3-127">Откройте портал Azure ([https://portal.azure.com](https://portal.azure.com)) на отдельной вкладке браузера. Если необходимо, выполните вход, используя данные учетной записи глобального администратора для пробной подписки на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-127">Create a separate tab in your browser, and then go to the Azure portal at https://portal.azure.com. If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="6b6e3-128">На портале Azure выберите **Azure Active Directory > Группы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-128">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
3. <span data-ttu-id="6b6e3-129">В колонке **Группы — Все группы** выберите пункт **+ Создать группу**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="6b6e3-130">В колонке **Группа**:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="6b6e3-131">В разделе **Тип группы** выберите **Office 365**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-131">Select **Office 365** in **Group type**.</span></span>
    
  - <span data-ttu-id="6b6e3-132">Введите **Топ-менеджмент** в поле **Имя**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-132">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="6b6e3-133">Выберите **Назначенные** в поле **Тип членства**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-133">Select **Assigned** in **Membership**.</span></span>
      
5. <span data-ttu-id="6b6e3-134">Нажмите кнопку **Создать**, а затем закройте колонку **Группа**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="6b6e3-135">Повторите шаги с 3 по 5 для следующих групп:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="6b6e3-136">ИТ-персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-136">IT staff</span></span>
    
  - <span data-ttu-id="6b6e3-137">Научный персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-137">Research staff</span></span>
    
  - <span data-ttu-id="6b6e3-138">Штатный персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-138">Regular staff</span></span>
    
  - <span data-ttu-id="6b6e3-139">Маркетинговый персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-139">Marketing staff</span></span>
    
  - <span data-ttu-id="6b6e3-140">Торговый персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-140">Sales staff</span></span>
    
7. <span data-ttu-id="6b6e3-141">Не закрывайте вкладку портала Azure в браузере.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="6b6e3-142">После этого настройте автоматическое лицензирование, чтобы членам групп автоматически назначались лицензии на подписки Office 365 и EMS.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="6b6e3-143">На портале Azure последовательно выберите **Azure Active Directory > Лицензии > Все продукты**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="6b6e3-144">В списке выберите **Enterprise Mobility + Security E5** и **Office 365 корпоративный E5** и нажмите **Назначить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="6b6e3-145">В колонке **Назначение лицензии** щелкните **Пользователи и группы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="6b6e3-146">В списке групп выберите следующие элементы:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="6b6e3-147">Высшее руководство</span><span class="sxs-lookup"><span data-stu-id="6b6e3-147">C-Suite</span></span>
    
  - <span data-ttu-id="6b6e3-148">ИТ-персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-148">IT staff</span></span>
    
  - <span data-ttu-id="6b6e3-149">Научный персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-149">Research staff</span></span>
    
  - <span data-ttu-id="6b6e3-150">Штатный персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-150">Regular staff</span></span>
    
  - <span data-ttu-id="6b6e3-151">Маркетинговый персонал</span><span class="sxs-lookup"><span data-stu-id="6b6e3-151">Marketing staff</span></span>
    
  - <span data-ttu-id="6b6e3-152">Сотрудники отдела продаж</span><span class="sxs-lookup"><span data-stu-id="6b6e3-152">Sales staff</span></span>
    
5. <span data-ttu-id="6b6e3-153">Выберите **Выбрать** > **Назначить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="6b6e3-154">Закройте вкладку портала Azure в браузере.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="6b6e3-155">Далее вы [подключитесь к модулю Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="6b6e3-156">Введите название организации, адрес и общий пароль и выполните эти команды в командной строке PowerShell или интегрированной среде сценариев (ISE), чтобы создать учетные записи пользователей и добавить их в свои группы:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-156">Fill in your organization name, your location, and a common password. Run the following commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their corresponding groups.</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> <span data-ttu-id="6b6e3-p103">Общий пароль используется для автоматизации и упрощения настройки среды разработки и тестирования. Не рекомендуется для рабочих подписок.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="6b6e3-159">Выполните указанные ниже действия, чтобы убедиться, что лицензирование на основе групп работает должным образом.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="6b6e3-160">На вкладке браузера **Домашняя страница Microsoft Office** щелкните плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="6b6e3-161">На новой вкладке браузера**Центр администрирования Office** щелкните **Пользователи**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="6b6e3-162">В списке пользователей выберите **Генеральный директор**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="6b6e3-163">В области, где приведены свойства учетной записи **Генеральный директор**, проверьте, что этой учетной записи назначены лицензии **Enterprise Mobility + Security E5** и **Office 365 корпоративный E5** лицензии (в разделе **Лицензии на продукты**).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="6b6e3-164">Этап 3. Создание меток Office 365</span><span class="sxs-lookup"><span data-stu-id="6b6e3-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="6b6e3-165">На этом этапе мы создадим метки разных уровней защиты для папок документов на сайтах групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="6b6e3-p104">Если необходимо, используйте частный экземпляр интернет-браузера и войдите на портал Office 365 с помощью учетной записи глобального администратора пробной подписки Office 365 E5. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6b6e3-168">На вкладке **Домашняя страница Microsoft Office** щелкните плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="6b6e3-169">На новой вкладке браузера **Центр администрирования Office** выберите **Центры администрирования > Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="6b6e3-170">На новой вкладке браузера **Главная — безопасность и соответствие требованиям** выберите **Классификации > Метки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="6b6e3-171">В области **Главная > Метки** нажмите кнопку **Создать метку**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="6b6e3-172">В области **Задайте имя для метки** введите **Внутренний общедоступный** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-172">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6b6e3-173">В области **Параметры метки** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="6b6e3-174">В области **Проверьте параметры** нажмите **Создать эту метку**, а затем — кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="6b6e3-175">Повторите действия 5–8 для следующих меток:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="6b6e3-176">Private</span><span class="sxs-lookup"><span data-stu-id="6b6e3-176">Private</span></span>
    
  - <span data-ttu-id="6b6e3-177">Конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="6b6e3-177">Sensitive</span></span>
    
  - <span data-ttu-id="6b6e3-178">Строго конфиденциально</span><span class="sxs-lookup"><span data-stu-id="6b6e3-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="6b6e3-179">В области **Главная > Метки** щелкните **Опубликовать метки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="6b6e3-180">В области **Выберите метки для публикации** щелкните **Выберите метки для публикации**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="6b6e3-181">В области **Выбор меток** нажмите кнопку **Добавить** и выберите все четыре метки.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="6b6e3-182">Нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="6b6e3-183">В области **Выберите метки для публикации** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="6b6e3-184">В области **Выберите расположения** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="6b6e3-185">В области **Укажите имя для политики** введите **Пример организации** в поле **Имя** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="6b6e3-186">В области **Проверьте параметры** последовательно нажмите кнопки **Опубликовать метки** и **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="6b6e3-187">Этап 4. Создание сайтов групп SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6b6e3-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="6b6e3-188">На этом этапе вы создадите и настроите четыре типа сайтов групп SharePoint Online для примера организации.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="6b6e3-189">Сайт группы "Для всей организации"</span><span class="sxs-lookup"><span data-stu-id="6b6e3-189">Organization wide team site</span></span>

<span data-ttu-id="6b6e3-190">Чтобы создать общедоступный сайт группы SharePoint Online с базовым уровнем защиты, выполните приведенные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="6b6e3-p105">Если необходимо, используйте браузер на локальном компьютере и войдите на портал Office 365 с помощью учетной записи глобального администратора. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6b6e3-193">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6b6e3-194">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6b6e3-195">На странице **Создание сайта** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6b6e3-196">В поле **Имя сайта** введите **Для всей организации**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="6b6e3-197">В поле **Описание сайта группы** введите **Сайт SharePoint для всей организации**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="6b6e3-198">В разделе **Параметры конфиденциальности** выберите **Общедоступная группа: все в организации имеют доступ к этому сайту** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6b6e3-199">В области **Кого вы хотите добавить?** нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="6b6e3-200">Далее настройте папку документов сайта группы "Для всей организации" для метки "Внутренний общедоступный".</span><span class="sxs-lookup"><span data-stu-id="6b6e3-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="6b6e3-201">На вкладке браузера **Для всей организации — главная** щелкните **Документы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-201">In the **Organization wide–Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="6b6e3-202">Щелкните значок параметров и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="6b6e3-203">В разделе **Разрешения и управление** нажмите **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="6b6e3-204">В разделе **Параметры — применение метки** выберите метку **Внутренний общедоступный** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-204">In **Settings-Apply Label**, select **Internal Public**, and click **Save**.</span></span>
    
<span data-ttu-id="6b6e3-205">Ниже показана полученная в итоге конфигурация.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-205">Here is your resulting configuration.</span></span>
  
![Защита базового уровня для общедоступного сайта группы SharePoint Online, используемого во всей организации.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="6b6e3-207">Сайт группы "Проект 1"</span><span class="sxs-lookup"><span data-stu-id="6b6e3-207">Project 1 team site</span></span>

<span data-ttu-id="6b6e3-208">Чтобы создать частный сайт группы SharePoint Online с базовым уровнем защиты для проекта в организации, выполните приведенные далее действия.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="6b6e3-p106">Если необходимо, используйте браузер на локальном компьютере и войдите на портал Office 365 с помощью учетной записи глобального администратора. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6b6e3-211">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6b6e3-212">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6b6e3-213">На странице **Создание сайта** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6b6e3-214">В поле **Имя сайта** введите **Проект 1**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="6b6e3-215">В поле **Описание сайта группы** введите **Сайт SharePoint для проекта 1**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-215">In **Team site description**, type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="6b6e3-216">В разделе **Параметры конфиденциальности** выберите **Закрытая группа: только участники имеют доступ к этому сайту** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6b6e3-217">В области **Кого вы хотите добавить?** нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="6b6e3-218">Далее настройте папку документов сайта группы "Проект 1" для метки "Частный".</span><span class="sxs-lookup"><span data-stu-id="6b6e3-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="6b6e3-219">На вкладке браузера **Проект 1 — главная** щелкните **Документы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="6b6e3-220">Щелкните значок параметров и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="6b6e3-221">В разделе **Разрешения и управление** нажмите кнопку **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="6b6e3-222">В разделе **Параметры — применение метки** выберите метку **Частный** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="6b6e3-223">Ниже показана полученная в итоге конфигурация.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-223">Here is your resulting configuration.</span></span>
  
![Защита базового уровня для закрытого сайта группы SharePoint Online, названного Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="6b6e3-225">Сайт группы "Маркетинговые кампании"</span><span class="sxs-lookup"><span data-stu-id="6b6e3-225">Marketing campaigns team site</span></span>

<span data-ttu-id="6b6e3-226">Чтобы создать изолированный сайт группы SharePoint Online с конфиденциальным уровнем защиты для участников маркетинговых кампаний, выполните приведенные далее действия.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="6b6e3-p107">Используя браузер на локальном компьютере, войдите на портал Office 365 с помощью учетной записи глобального администратора. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6b6e3-229">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6b6e3-230">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6b6e3-231">На странице **Создание сайта** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6b6e3-232">В поле **Имя сайта группы** введите **Маркетинговые кампании**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="6b6e3-233">В поле **Описание сайта группы** введите **Сайт SharePoint для участников маркетинговых кампаний (конфиденциальный)**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="6b6e3-234">В разделе **Параметры конфиденциальности** выберите **Закрытая группа: только участники имеют доступ к этому сайту** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6b6e3-235">В области **Кого вы хотите добавить?** нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="6b6e3-236">Перейдите к новой вкладке **Маркетинговые кампании** в браузере, а затем на панели инструментов нажмите значок параметров и выберите **Разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="6b6e3-237">В области **Разрешения для сайта** щелкните **Параметры дополнительных разрешений**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="6b6e3-238">На новой вкладке браузера **Разрешения** щелкните **Параметры запросов на доступ**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="6b6e3-239">В диалоговом окне **Параметры запросов на доступ** снимите флажки **Разрешить участникам совместный доступ к этому сайту, а также отдельным файлам и папкам** и **Разрешить участникам приглашать других пользователей в группу участников сайта**, введите **ITAdmin1@**\<название_организации>**.onmicrosoft.com** в поле **Отправлять все запросы на доступ по следующему адресу электронной почты**, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-239">In the Access Request Settings dialog box, clear the Allow members to share the site and individual files and folders and Allow members to invite others to the site members group check boxes, type ITAdmin1@<your organization name>.onmicrosoft.com in Send all requests for access, and then click OK.</span></span>
    
13. <span data-ttu-id="6b6e3-240">В списке выберите пункт **Маркетинговые кампании — участники**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="6b6e3-241">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="6b6e3-242">В диалоговом окне **Общий доступ** введите **Сотрудники отдела маркетинга**, выберите эту группу и нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="6b6e3-243">Повторите этапы 14 и 15 для учетной записи пользователя **Исследователь1**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="6b6e3-244">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="6b6e3-245">Выберите в списке пункт **Маркетинговые кампании — владельцы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="6b6e3-246">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="6b6e3-247">В диалоговом окне **Общий доступ** введите **ИТ-персонал**, выберите группу и нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="6b6e3-248">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="6b6e3-249">Закройте вкладку **Пользователи и группы** в браузере, перейдите на вкладку **Маркетинговые кампании — главная** в браузере и закройте область **Разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="6b6e3-250">Ниже представлены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="6b6e3-251">Группа SharePoint **Маркетинговые кампании — участники** содержит только группу **Маркетинговые кампании** (в которой находится учетная запись глобального администратора), группу **Маркетинговый персонал** (в которой находятся учетные записи пользователей Marketing1 и Marketing2) и учетную запись пользователя **Researcher1**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="6b6e3-252">Группа SharePoint **Маркетинговые кампании — владельцы** содержит только группу **ИТ-персонал** (в которой находятся только учетные записи пользователей ITAdmin1 и ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="6b6e3-253">Группа SharePoint **Маркетинговые кампании — посетители** не содержит групп или учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="6b6e3-254">Участники не могут изменять разрешения уровня веб-сайта (это могут делать только члены группы **Маркетинговые кампании — владельцы**).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="6b6e3-255">У других учетных записей нет доступа к сайту и его ресурсам, но они могут запрашивать доступ к сайту. При этом в почтовый ящик пользователя "ИТ-администратор1" отправляется электронное сообщение.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="6b6e3-256">Теперь настройте папку документов на сайте группы "Маркетинговые кампании" на использование метки "Конфиденциальный".</span><span class="sxs-lookup"><span data-stu-id="6b6e3-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="6b6e3-257">На вкладке браузера **Маркетинговые кампании — главная** щелкните **Документы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="6b6e3-258">Щелкните значок параметров и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="6b6e3-259">В разделе **Разрешения и управление** нажмите кнопку **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="6b6e3-260">В разделе **Параметры — применение метки** выберите метку **Конфиденциальный** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="6b6e3-261">Настройте политику защиты от потери данных (DLP), которая уведомляет пользователей, когда они предоставляют общий доступ к документу на сайте группы SharePoint Online с меткой "Конфиденциальный" (в число таких сайтов входит сайт "Маркетинговые кампании") за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="6b6e3-262">На вкладке браузера **Домашняя страница Microsoft Office** щелкните плитку **Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="6b6e3-263">На новой вкладке **Безопасность и соответствие требованиям** выберите **Защита от потери данных > Политика**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="6b6e3-264">В области **Защита от потери данных** нажмите кнопку **+ Создание политики**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="6b6e3-265">В области **Начать с шаблона или создать настраиваемую политику** выберите **Настраиваемая**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="6b6e3-266">В области **Назовите политику** введите **Сайты групп SharePoint Online с меткой "Конфиденциальный"** в поле **Имя**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="6b6e3-267">В области **Выберите расположения** щелкните **Позволить мне выбрать расположения** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6b6e3-268">В списке расположений отключите параметры **Электронная почта Exchange** и **Учетные записи OneDrive**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6b6e3-269">В области **Выберите тип содержимого, которое вы хотите защитить** щелкните ссылку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="6b6e3-270">В области **Выбрать типы содержимого для защиты** выберите **Добавить** в раскрывающемся списке, а затем выберите **Метки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="6b6e3-271">В области **Метки** нажмите кнопку **+ Добавить**, укажите метку **Конфиденциальный** и последовательно нажмите кнопки **Добавить** > **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="6b6e3-272">В области **Выбрать типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="6b6e3-273">В области **Customize the types of sensitive info you want to protect** (Настройка типов защищаемых конфиденциальных сведений) нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="6b6e3-274">В области **What do you want to do if we detect sensitive info?** (Что делать при обнаружении конфиденциальной информации?) щелкните **Customize the tip and email** (Настроить подсказки и уведомления по электронной почте).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="6b6e3-275">В области **Customize policy tips and email notifications** (Настройка подсказок политики и уведомления по электронной почте) щелкните **Customize the policy tip text** (Настроить текст подсказки политики).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="6b6e3-276">В текстовом поле введите или вставьте следующее:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="6b6e3-p108">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="6b6e3-280">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="6b6e3-281">В области **Что делать при обнаружении конфиденциальной информации?** снимите флажки **Запретить пользователям делиться контентом и ограничить доступ к совместно используемому содержимому**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="6b6e3-282">В области **Включить политику или сначала протестировать ее?** выберите пункт **Да, включить ее сразу**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6b6e3-283">В области **Проверка параметров** нажмите **Создать**, а затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="6b6e3-284">Ниже показана полученная в итоге конфигурация.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-284">Here is your resulting configuration.</span></span>
  
![Защита уровня конфиденциальности для изолированного сайта группы SharePoint Online, названного "Маркетинговые кампании".](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="6b6e3-286">Сайт группы "Стратегия организации"</span><span class="sxs-lookup"><span data-stu-id="6b6e3-286">Company strategy team site</span></span>

<span data-ttu-id="6b6e3-287">Чтобы создать изолированный сайт группы SharePoint Online со строго конфиденциальным уровнем защиты для стратегических ресурсов организации, включающих высшее руководство, выполните приведенные далее действия.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="6b6e3-p109">Если необходимо, используйте браузер на локальном компьютере и войдите на портал Office 365 с помощью учетной записи глобального администратора. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6b6e3-290">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6b6e3-291">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6b6e3-292">На странице **Создание сайта** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6b6e3-293">В поле **Имя сайта группы** введите **Стратегия организации**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="6b6e3-294">В поле **Описание сайта группы** введите **Сайт SharePoint для стратегии организации (строго конфиденциальный)**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="6b6e3-295">В разделе **Параметры конфиденциальности** выберите **Закрытая группа: только участники имеют доступ к этому сайту** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6b6e3-296">В области **Кого вы хотите добавить?** нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="6b6e3-297">В новой вкладке **Стратегия компании** в браузере нажмите значок параметров на панели инструментов и выберите **Разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="6b6e3-298">В области **Разрешения для сайта** щелкните **Параметры дополнительных разрешений**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="6b6e3-299">На новой вкладке браузера **Разрешения** щелкните **Параметры запросов на доступ**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="6b6e3-300">В диалоговом окне **Параметры запросов на доступ** снимите флажки **Разрешить участникам совместный доступ к этому сайту, а также отдельным файлам и папкам** и **Разрешить участникам приглашать других пользователей в группу участников сайта** (все три флажка должны быть сняты) и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="6b6e3-301">Выберите в списке пункт **Стратегия компании — участники**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="6b6e3-302">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="6b6e3-303">В диалоговом окне **Общий доступ** введите **Топ-менеджмент**, выберите группу и нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="6b6e3-304">Выберите в списке пункт **Стратегия компании — владельцы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="6b6e3-305">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="6b6e3-306">В диалоговом окне **Общий доступ** введите **ИТ-персонал**, выберите группу и нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="6b6e3-307">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="6b6e3-308">Закройте вкладку **Пользователи и группы** в браузере, перейдите на вкладку **Стратегия компании — главная** в браузере и закройте область **Разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="6b6e3-309">Ниже приведены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="6b6e3-310">Группа SharePoint **Стратегия организации — участники** содержит только группу **Высшее руководство** (в которую входят только учетные записи генерального директора, финансового директора и директора по информационным технологиям) и группу **Стратегия организации** (в которую входит только учетная запись глобального администратора).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="6b6e3-311">Группа SharePoint **Стратегия организации — владельцы** содержит только группу **ИТ-персонал** (в которой находятся только учетные записи пользователей "ITAdmin1" и "ITAdmin2").</span><span class="sxs-lookup"><span data-stu-id="6b6e3-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="6b6e3-312">Группа SharePoint **Стратегия организации — посетители** не содержит групп или учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="6b6e3-313">Участники не могут изменять разрешения уровня веб-сайта (это могут делать только члены группы **Стратегия организации — владельцы**).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="6b6e3-p110">Другие учетные записи пользователей не могут получить доступ к сайту или его ресурсам или запросить доступ к сайту. Дополнительные разрешения для сайта должен назначить глобальный администратор или участник группы **Стратегия организации — владельцы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="6b6e3-316">Затем настройте папку документов на сайте стратегической группы компании на использование метки "Строго конфиденциально".</span><span class="sxs-lookup"><span data-stu-id="6b6e3-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="6b6e3-317">На вкладке браузера **Стратегия организации — главная** щелкните **Документы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="6b6e3-318">Щелкните значок параметров и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="6b6e3-319">В разделе **Разрешения и управление** нажмите кнопку **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="6b6e3-320">В разделе **Параметры — применение метки** выберите метку **Строго конфиденциальный** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="6b6e3-321">Настройте политику защиты от потери данных (DLP), которая блокирует пользователей, когда они предоставляют общий доступ к документу на сайте группы SharePoint Online с меткой "Строго конфиденциальный" (в число таких сайтов входит сайт "Стратегия организации") за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="6b6e3-p111">Если необходимо, используйте браузер на локальном компьютере и войдите на портал Office 365 с помощью учетной записи с ролью администратора безопасности или администратора организации. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6b6e3-324">На вкладке браузера **Домашняя страница Microsoft Office** щелкните плитку **Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="6b6e3-325">На новой вкладке **Безопасность и соответствие требованиям** выберите **Защита от потери данных > Политика**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="6b6e3-326">В области **Защита от потери данных** нажмите кнопку **+ Создание политики**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="6b6e3-327">В области **Начать с шаблона или создать настраиваемую политику** выберите **Настраиваемая**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="6b6e3-328">В области **Назовите политику** введите **Сайты групп SharePoint Online с меткой "Строго конфиденциальный"** в поле **Имя**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6b6e3-329">В области **Выберите расположения** щелкните **Позволить мне выбрать расположения** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6b6e3-330">В списке расположений отключите параметры **Электронная почта Exchange** и **Учетные записи OneDrive**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="6b6e3-331">В области **Выберите тип содержимого, которое вы хотите защитить** щелкните ссылку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="6b6e3-332">В области **Выбрать типы содержимого для защиты** выберите **Добавить** в раскрывающемся списке, а затем выберите **Метки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="6b6e3-333">В области **Метки** нажмите кнопку **+ Добавить**, выберите метку **Строго конфиденциальный**, нажмите **Добавить**, а затем нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="6b6e3-334">В области **Выбрать типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="6b6e3-335">В области **Customize the types of sensitive info you want to protect** (Настройка типов защищаемых конфиденциальных сведений) нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="6b6e3-336">В области **What do you want to do if we detect sensitive info?** (Что делать при обнаружении конфиденциальной информации?) щелкните **Customize the tip and email** (Настроить подсказки и уведомления по электронной почте).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="6b6e3-337">В области **Customize policy tips and email notifications** (Настройка подсказок политики и уведомления по электронной почте) щелкните **Customize the policy tip text** (Настроить текст подсказки политики).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="6b6e3-338">В текстовом поле введите или вставьте следующее:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="6b6e3-p112">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="6b6e3-342">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="6b6e3-343">В области **Что делать при обнаружении конфиденциальной информации?** выберите **Требовать коммерческое обоснование для переопределения**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6b6e3-344">В области **Включить политику или сначала протестировать ее?** выберите пункт **Да, включить ее сразу**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="6b6e3-345">В области **Проверка параметров** нажмите **Создать**, а затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="6b6e3-346">Далее выполните инструкции в статье [Активация Azure RMS с помощью Центра администрирования Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="6b6e3-347">Затем настройте для Azure Information Protection новую политику области и вложенную метку для группы "Топ-менеджмент" для защиты и разрешений, выполнив следующие действия:</span><span class="sxs-lookup"><span data-stu-id="6b6e3-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="6b6e3-p113">Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6b6e3-350">Перейдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), открыв отдельную вкладку браузера.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="6b6e3-351">Если вы настраиваете Azure Information Protection впервые, ознакомьтесь с этими [инструкциями](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="6b6e3-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="6b6e3-352">На панели списка выберите **Все службы**, введите **information**, а затем выберите **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>

5. <span data-ttu-id="6b6e3-353">Выберите **Метки**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-353">Click **Labels**.</span></span>
    
6. <span data-ttu-id="6b6e3-354">Щелкните правой кнопкой мыши метку **Строго конфиденциально** и выберите элемент **Добавить подчин. метку**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-354">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
7. <span data-ttu-id="6b6e3-355">Введите **Представители топ-менеджмента** в полях **Имя** и **Описание**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-355">Type **C-Suite members** in **Name** and **Description**.</span></span>
    
8. <span data-ttu-id="6b6e3-356">В разделе **Задайте разрешения для документов и электронных писем, имеющих эту метку** нажмите кнопку **Защитить**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-356">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
9. <span data-ttu-id="6b6e3-357">В разделе **Защита** выберите элемент **Azure (облачный ключ)**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-357">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
10. <span data-ttu-id="6b6e3-358">В колонке **Защита** в разделе **Параметры защиты** нажмите кнопку **+ Добавить разрешения**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-358">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
11. <span data-ttu-id="6b6e3-359">Перейдите к колонке **Добавление разрешений** и выберите **+ Обзор каталога** в разделе **Укажите пользователей и группы**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-359">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
12. <span data-ttu-id="6b6e3-360">В области **Пользователи и группы AAD** выберите группу **Топ-менеджмент** и нажмите кнопку **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-360">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
13. <span data-ttu-id="6b6e3-361">В разделе **Выбрать из предустановленных разрешений или задать пользовательские** выберите вариант **Пользовательские**, а затем установите флажки **Просмотреть права**, **Изменить контент**, **Сохранить**, **Ответить** и **Ответить всем**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-361">Under **Choose permissions from the preset or set custom**, click **Custom**, and then click the **View Rights**, **Edit Content**, **Save**, **Reply**, and **Reply all** check boxes.</span></span>
    
14. <span data-ttu-id="6b6e3-362">Дважды нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-362">Click **OK** twice.</span></span>
    
15. <span data-ttu-id="6b6e3-363">В колонке **Подчиненная метка** нажмите кнопку **Сохранить**, а затем щелкните **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-363">On the **Sub-label** blade, click **Save**, and then click **OK**.</span></span>

16. <span data-ttu-id="6b6e3-364">В колонке **Azure Information Protection**, щелкните элементы **Политики > + Добавить политику**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-364">On the **Azure Information protection** blade, click **Scoped policies > + Add a new policy**.</span></span>
    
17. <span data-ttu-id="6b6e3-365">Введите **CompanyStrategy** в поле **Имя политики** и **Метка для документов на сайте группы стратегии компании** в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-365">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
18. <span data-ttu-id="6b6e3-366">Щелкните пункты **"Выберите, к каким пользователям или группам будет применяться эта политика" > "Пользователи или группы"**, а затем выберите **C-Suite**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-366">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
19. <span data-ttu-id="6b6e3-367">Щелкните **Выбрать > ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-367">Click **Select > OK**.</span></span>

20. <span data-ttu-id="6b6e3-p114">Выберите элемент **Добавить или удалить метки**. В панели **Политики: добавление и удаление меток** нажмите **Топ-менеджмент**, а затем — **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-p114">Click **Add or remove labels**. In the **Policy: Add or remove labels** pane, click **C-Suite**, and then click **OK**.</span></span>   

21. <span data-ttu-id="6b6e3-370">Нажмите кнопку **Сохранить**, а затем — **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-370">Click **Apply**, and then click **OK**.</span></span>
    
<span data-ttu-id="6b6e3-371">Чтобы защитить документ с помощью Azure Information Protection и новой метки, необходимо [установить клиент Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) на тестовом компьютере, установить Office из портала Office 365 и затем выполнить вход из Microsoft Word с помощью учетной записи в группе **Топ-менеджмент** пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-371">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
<span data-ttu-id="6b6e3-372">Ниже показана полученная в итоге конфигурация.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-372">Here is your resulting configuration.</span></span>
  
![Защита уровня строгой конфиденциальности для изолированного сайта группы SharePoint Online, названного "Стратегия компании".](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="6b6e3-374">Теперь вы готовы к созданию документов на этих четырех сайтах и тестированию доступа к ним с помощью различных учетных записей пользователей в пробной подписке.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-374">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="6b6e3-375">Здесь приведена общая конфигурация для всех четырех сайтов групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-375">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Все четыре сайта группы в безопасной среде разработки и тестирования SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="6b6e3-377">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="6b6e3-377">Next step</span></span>

<span data-ttu-id="6b6e3-378">Когда вы будете готовы к выполнению рабочего развертывания безопасных сайтов SharePoint Online, прочтите статью [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) (Защита сайтов и файлов SharePoint Online), содержащую подробные сведения и ссылки на статьи с пошаговыми руководствами.</span><span class="sxs-lookup"><span data-stu-id="6b6e3-378">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6b6e3-379">См. также</span><span class="sxs-lookup"><span data-stu-id="6b6e3-379">See Also</span></span>

[<span data-ttu-id="6b6e3-380">Безопасность сайтов и файлов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6b6e3-380">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="6b6e3-381">Решения для обеспечения безопасности</span><span class="sxs-lookup"><span data-stu-id="6b6e3-381">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="6b6e3-382">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="6b6e3-382">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="6b6e3-383">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="6b6e3-383">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




