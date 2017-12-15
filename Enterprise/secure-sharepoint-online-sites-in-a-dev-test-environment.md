---
title: "Защита сайтов SharePoint Online в среде разработки и тестирования"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Summary: Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.'
ms.openlocfilehash: 17abee7a293996194a097693607b4b4d9c117046
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="d4722-103">Защита сайтов SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="d4722-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="d4722-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span><span class="sxs-lookup"><span data-stu-id="d4722-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="d4722-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span><span class="sxs-lookup"><span data-stu-id="d4722-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![Все четыре сайта группы в безопасной среде разработки и тестирования SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="d4722-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span><span class="sxs-lookup"><span data-stu-id="d4722-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="d4722-108">Этап 1. Создание среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="d4722-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="d4722-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span><span class="sxs-lookup"><span data-stu-id="d4722-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="d4722-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d4722-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="d4722-111">Затем оформите пробную подписку на EMS и добавьте ее к той же организации, что и пробную подписку на Office 365.</span><span class="sxs-lookup"><span data-stu-id="d4722-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="d4722-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d4722-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d4722-114">Click the **Admin** tile.</span><span class="sxs-lookup"><span data-stu-id="d4722-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="d4722-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span><span class="sxs-lookup"><span data-stu-id="d4722-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="d4722-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span><span class="sxs-lookup"><span data-stu-id="d4722-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="d4722-118">On the **Confirm your order** page, click **Try now**.</span><span class="sxs-lookup"><span data-stu-id="d4722-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="d4722-119">On the **Order receipt** page, click **Continue**.</span><span class="sxs-lookup"><span data-stu-id="d4722-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="d4722-120">Затем включите лицензию на Enterprise Mobility + Security E5 для учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="d4722-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="d4722-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span><span class="sxs-lookup"><span data-stu-id="d4722-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="d4722-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span><span class="sxs-lookup"><span data-stu-id="d4722-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="d4722-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span><span class="sxs-lookup"><span data-stu-id="d4722-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="d4722-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span><span class="sxs-lookup"><span data-stu-id="d4722-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="d4722-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span><span class="sxs-lookup"><span data-stu-id="d4722-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="d4722-126">First, create a set of groups for a typical organization with the Azure portal.</span><span class="sxs-lookup"><span data-stu-id="d4722-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="d4722-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span><span class="sxs-lookup"><span data-stu-id="d4722-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="d4722-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span><span class="sxs-lookup"><span data-stu-id="d4722-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="d4722-129">On the **All groups** blade, click **+ New group**.</span><span class="sxs-lookup"><span data-stu-id="d4722-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="d4722-130">On the **Group** blade:</span><span class="sxs-lookup"><span data-stu-id="d4722-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="d4722-131">Type **C-Suite** in **Name**.</span><span class="sxs-lookup"><span data-stu-id="d4722-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="d4722-132">Select **Assigned** in **Membership**.</span><span class="sxs-lookup"><span data-stu-id="d4722-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="d4722-133">Click **Yes** for **Enable Office features**.</span><span class="sxs-lookup"><span data-stu-id="d4722-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="d4722-134">Click **Create**, and then close the **Group** blade.</span><span class="sxs-lookup"><span data-stu-id="d4722-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="d4722-135">Repeat steps 3-5 for the following group names:</span><span class="sxs-lookup"><span data-stu-id="d4722-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="d4722-136">ИТ-персонал</span><span class="sxs-lookup"><span data-stu-id="d4722-136">IT staff</span></span>
    
  - <span data-ttu-id="d4722-137">Исследовательский персонал</span><span class="sxs-lookup"><span data-stu-id="d4722-137">Research staff</span></span>
    
  - <span data-ttu-id="d4722-138">Обычный персонал</span><span class="sxs-lookup"><span data-stu-id="d4722-138">Regular staff</span></span>
    
  - <span data-ttu-id="d4722-139">Сотрудники отдела маркетинга</span><span class="sxs-lookup"><span data-stu-id="d4722-139">Marketing staff</span></span>
    
  - <span data-ttu-id="d4722-140">Сотрудники отдела продаж</span><span class="sxs-lookup"><span data-stu-id="d4722-140">Sales staff</span></span>
    
7. <span data-ttu-id="d4722-141">Keep the Azure portal tab in your browser open.</span><span class="sxs-lookup"><span data-stu-id="d4722-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="d4722-142">Затем настройте автоматическое лицензирование, чтобы членам групп автоматически назначались лицензии для подписок на Office 365 и EMS.</span><span class="sxs-lookup"><span data-stu-id="d4722-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="d4722-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span><span class="sxs-lookup"><span data-stu-id="d4722-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="d4722-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span><span class="sxs-lookup"><span data-stu-id="d4722-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="d4722-145">In the **Assign license** blade, click **Users and groups**.</span><span class="sxs-lookup"><span data-stu-id="d4722-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="d4722-146">В списке выберите следующие группы:</span><span class="sxs-lookup"><span data-stu-id="d4722-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="d4722-147">Топ-менеджмент</span><span class="sxs-lookup"><span data-stu-id="d4722-147">C-Suite</span></span>
    
  - <span data-ttu-id="d4722-148">ИТ-персонал</span><span class="sxs-lookup"><span data-stu-id="d4722-148">IT staff</span></span>
    
  - <span data-ttu-id="d4722-149">Исследовательский персонал</span><span class="sxs-lookup"><span data-stu-id="d4722-149">Research staff</span></span>
    
  - <span data-ttu-id="d4722-150">Обычный персонал</span><span class="sxs-lookup"><span data-stu-id="d4722-150">Regular staff</span></span>
    
  - <span data-ttu-id="d4722-151">Сотрудники отдела маркетинга</span><span class="sxs-lookup"><span data-stu-id="d4722-151">Marketing staff</span></span>
    
  - <span data-ttu-id="d4722-152">Сотрудники отдела продаж</span><span class="sxs-lookup"><span data-stu-id="d4722-152">Sales staff</span></span>
    
5. <span data-ttu-id="d4722-153">Click **Select**, and then click **Assign**.</span><span class="sxs-lookup"><span data-stu-id="d4722-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="d4722-154">Закройте вкладку портала Azure в браузере.</span><span class="sxs-lookup"><span data-stu-id="d4722-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="d4722-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="d4722-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="d4722-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span><span class="sxs-lookup"><span data-stu-id="d4722-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
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
> <span data-ttu-id="d4722-p103">Общий пароль используется для автоматизации и упрощения настройки среды разработки и тестирования. Не рекомендуется для рабочих подписок.</span><span class="sxs-lookup"><span data-stu-id="d4722-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="d4722-159">Выполните указанные ниже действия, чтобы убедиться, что лицензирование на основе групп работает должным образом.</span><span class="sxs-lookup"><span data-stu-id="d4722-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="d4722-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span><span class="sxs-lookup"><span data-stu-id="d4722-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="d4722-161">From the new **Office Admin center** tab of your browser, click **Users**.</span><span class="sxs-lookup"><span data-stu-id="d4722-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="d4722-162">In the list of users, click **CEO**.</span><span class="sxs-lookup"><span data-stu-id="d4722-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="d4722-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span><span class="sxs-lookup"><span data-stu-id="d4722-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="d4722-164">Phase 3: Create Office 365 labels</span><span class="sxs-lookup"><span data-stu-id="d4722-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="d4722-165">На этом этапе мы создадим метки разных уровней защиты для папок документов на сайтах групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d4722-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="d4722-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d4722-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d4722-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span><span class="sxs-lookup"><span data-stu-id="d4722-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="d4722-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="d4722-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="d4722-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span><span class="sxs-lookup"><span data-stu-id="d4722-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="d4722-171">From the **Home > Labels** pane, click **Create a label**.</span><span class="sxs-lookup"><span data-stu-id="d4722-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="d4722-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span><span class="sxs-lookup"><span data-stu-id="d4722-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d4722-173">On the **Label settings** pane, click **Next**.</span><span class="sxs-lookup"><span data-stu-id="d4722-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="d4722-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span><span class="sxs-lookup"><span data-stu-id="d4722-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="d4722-175">Повторите действия 5–8 для следующих меток:</span><span class="sxs-lookup"><span data-stu-id="d4722-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="d4722-176">Частный</span><span class="sxs-lookup"><span data-stu-id="d4722-176">Private</span></span>
    
  - <span data-ttu-id="d4722-177">Конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="d4722-177">Sensitive</span></span>
    
  - <span data-ttu-id="d4722-178">Строго конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="d4722-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="d4722-179">From the **Home > Labels** pane, click **Publish labels**.</span><span class="sxs-lookup"><span data-stu-id="d4722-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="d4722-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span><span class="sxs-lookup"><span data-stu-id="d4722-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="d4722-181">On the **Choose labels** pane, click **Add** and select all four labels.</span><span class="sxs-lookup"><span data-stu-id="d4722-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="d4722-182">Click **Done**.</span><span class="sxs-lookup"><span data-stu-id="d4722-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="d4722-183">On the **Choose labels to publish** pane, click **Next**.</span><span class="sxs-lookup"><span data-stu-id="d4722-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="d4722-184">On the **Choose locations** pane, click **Next**.</span><span class="sxs-lookup"><span data-stu-id="d4722-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="d4722-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span><span class="sxs-lookup"><span data-stu-id="d4722-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="d4722-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span><span class="sxs-lookup"><span data-stu-id="d4722-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="d4722-187">Phase 4: Create your SharePoint Online team sites</span><span class="sxs-lookup"><span data-stu-id="d4722-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="d4722-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span><span class="sxs-lookup"><span data-stu-id="d4722-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="d4722-189">Сайт группы для всей организации</span><span class="sxs-lookup"><span data-stu-id="d4722-189">Organization wide team site</span></span>

<span data-ttu-id="d4722-190">Чтобы создать базовый общедоступный сайт группы SharePoint Online, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="d4722-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="d4722-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d4722-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d4722-193">In the list of tiles, click **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d4722-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d4722-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span><span class="sxs-lookup"><span data-stu-id="d4722-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d4722-195">On the **Create a site** page, click **Team site**.</span><span class="sxs-lookup"><span data-stu-id="d4722-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d4722-196">In **Site name**, type **Organization wide**.</span><span class="sxs-lookup"><span data-stu-id="d4722-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="d4722-197">In **Team site description**, type **SharePoint site for the entire organization**.</span><span class="sxs-lookup"><span data-stu-id="d4722-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="d4722-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span><span class="sxs-lookup"><span data-stu-id="d4722-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d4722-199">On the **Who do you want to add?** pane, click **Finish**.</span><span class="sxs-lookup"><span data-stu-id="d4722-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="d4722-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span><span class="sxs-lookup"><span data-stu-id="d4722-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="d4722-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span><span class="sxs-lookup"><span data-stu-id="d4722-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d4722-202">Click the settings icon, and then click **Library settings**.</span><span class="sxs-lookup"><span data-stu-id="d4722-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d4722-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span><span class="sxs-lookup"><span data-stu-id="d4722-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d4722-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span><span class="sxs-lookup"><span data-stu-id="d4722-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="d4722-205">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="d4722-205">Here is your resulting configuration.</span></span>
  
![Защита базового уровня для общедоступного сайта группы SharePoint Online, используемого во всей организации.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="d4722-207">Сайт группы "Проект 1"</span><span class="sxs-lookup"><span data-stu-id="d4722-207">Project 1 team site</span></span>

<span data-ttu-id="d4722-208">Чтобы создать базовый частный сайт группы SharePoint Online для проекта в организации, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="d4722-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="d4722-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d4722-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d4722-211">In the list of tiles, click **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d4722-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d4722-212">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="d4722-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d4722-213">On the **Create a site** page, click **Team site**.</span><span class="sxs-lookup"><span data-stu-id="d4722-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d4722-214">В поле **имя узла**введите **1 для Project**.</span><span class="sxs-lookup"><span data-stu-id="d4722-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="d4722-215">В **поле Описание сайта группы** укажите **сайт SharePoint для проекта 1**.</span><span class="sxs-lookup"><span data-stu-id="d4722-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="d4722-216">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d4722-217">On the **Who do you want to add?** pane, click **Finish**.</span><span class="sxs-lookup"><span data-stu-id="d4722-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="d4722-218">Затем настройте папку документов на сайте группы "Проект 1" на использование метки "Частный".</span><span class="sxs-lookup"><span data-stu-id="d4722-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="d4722-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span><span class="sxs-lookup"><span data-stu-id="d4722-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d4722-220">Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="d4722-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d4722-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span><span class="sxs-lookup"><span data-stu-id="d4722-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d4722-222">В поле **Применить параметры метки**выберите **частный**и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="d4722-223">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="d4722-223">Here is your resulting configuration.</span></span>
  
![Защита базового уровня для закрытого сайта группы SharePoint Online, названного Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="d4722-225">Сайт группы маркетинговых кампаний</span><span class="sxs-lookup"><span data-stu-id="d4722-225">Marketing campaigns team site</span></span>

<span data-ttu-id="d4722-226">Чтобы создать изолированный сайт группы SharePoint Online на конфиденциальном уровне для ресурсов маркетинговых кампаний, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="d4722-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="d4722-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d4722-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d4722-229">In the list of tiles, click **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d4722-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d4722-230">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="d4722-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d4722-231">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="d4722-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d4722-232">In **Team site name**, type **Marketing campaigns**.</span><span class="sxs-lookup"><span data-stu-id="d4722-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="d4722-233">В поле **Описание сайта группы**укажите **сайт SharePoint для маркетинговых кампаний ресурсы (с учетом)**.</span><span class="sxs-lookup"><span data-stu-id="d4722-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="d4722-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span><span class="sxs-lookup"><span data-stu-id="d4722-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d4722-235">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="d4722-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="d4722-236">На вкладке **маркетинговые кампании** в браузере, в панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="d4722-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="d4722-237">В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="d4722-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="d4722-238">На новой вкладке **разрешения** в браузере нажмите кнопку **Параметры запроса доступа**.</span><span class="sxs-lookup"><span data-stu-id="d4722-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="d4722-239">В диалоговом окне **Параметры запроса доступа** снимите флажки **Разрешить членам для совместного использования сайтов и отдельных файлов и папок** и **Разрешить участникам приглашать других людей для группы участников сайта** введите **ITAdmin1 @**\<вашей Название организации >**. onmicrosoft.com** в **отправлять все запросы на доступ**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d4722-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="d4722-240">**Маркетинговые кампании элементы** выберите в списке.</span><span class="sxs-lookup"><span data-stu-id="d4722-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="d4722-241">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="d4722-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="d4722-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span><span class="sxs-lookup"><span data-stu-id="d4722-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="d4722-243">Повторите шаги 14 и 15 для учетной записи пользователя **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="d4722-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="d4722-244">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="d4722-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="d4722-245">**Маркетинговые кампании владельцев** выберите в списке.</span><span class="sxs-lookup"><span data-stu-id="d4722-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="d4722-246">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="d4722-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="d4722-247">В диалоговом окне **общий доступ** введите **ИТ-специалистов**, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="d4722-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="d4722-248">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="d4722-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="d4722-249">Закройте вкладку **людей и групп** в браузере, перейдите на вкладку **маркетинговых кампаний домашней** в браузере, а затем закройте в области **разрешения для сайта** .</span><span class="sxs-lookup"><span data-stu-id="d4722-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="d4722-250">Ниже представлены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="d4722-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="d4722-251">SharePoint **Маркетинговые кампании — члены** группы содержит только группе **маркетинговые кампании** (содержащий учетная запись глобального администратора), группа **сотрудников отдела маркетинга** , (который содержит Marketing1 и Marketing2 пользователя учетные записи), а **Researcher1** учетная запись пользователя.</span><span class="sxs-lookup"><span data-stu-id="d4722-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="d4722-252">**Маркетинговые кампании владельцев** SharePoint группа содержит только группы **ИТ-специалистов** (который содержит только ITAdmin1 и ITAdmin2 учетные записи пользователей).</span><span class="sxs-lookup"><span data-stu-id="d4722-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="d4722-253">Группы SharePoint **Маркетинговые кампании посетители** не содержит групп или учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="d4722-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="d4722-254">Члены не могут изменять разрешения на уровне сайта (это может быть выполнено только члены группы **Маркетинговые кампании владельцев** ).</span><span class="sxs-lookup"><span data-stu-id="d4722-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="d4722-255">У других учетных записей нет доступа к сайту и его ресурсам, но они могут запрашивать доступ к сайту. При этом в почтовый ящик пользователя "ИТ-администратор1" отправляется электронное сообщение.</span><span class="sxs-lookup"><span data-stu-id="d4722-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="d4722-256">Теперь настройте папку документов на сайте группы "Маркетинговые кампании" на использование метки "Конфиденциальный".</span><span class="sxs-lookup"><span data-stu-id="d4722-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="d4722-257">На вкладке **маркетинговых кампаний домашней** браузера щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="d4722-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d4722-258">Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="d4722-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d4722-259">В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="d4722-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d4722-260">В поле **Применить параметры метки**выберите **конфиденциальных**и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="d4722-261">Затем настройте политику защиты от потери данных (DLP), которая сообщает пользователям, когда они пытаются поделиться документом, хранящемся на сайте группы SharePoint Online с меткой "Конфиденциальный" (таким является и сайт "Маркетинговые кампании"), с пользователями за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="d4722-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="d4722-262">На вкладке **Microsoft Office для дома** в браузере выберите **безопасности &amp; соответствия** заголовков.</span><span class="sxs-lookup"><span data-stu-id="d4722-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="d4722-263">В новом **безопасности &amp; соответствия** в браузере, щелкните **защиту от потери данных > политики**.</span><span class="sxs-lookup"><span data-stu-id="d4722-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="d4722-264">На левой панели **защиту от потери данных** нажмите кнопку **+ Создать политику**.</span><span class="sxs-lookup"><span data-stu-id="d4722-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="d4722-265">В **Начать с шаблоном или создайте пользовательскую политику** области, выберите **настраиваемые**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="d4722-266">В области **Имя политики** введите **конфиденциальных метки SharePoint Online веб-сайтов групп** в поле **имя**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d4722-267">На левой панели **Выберите расположение** нажмите кнопку **выбрать определенные расположения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d4722-268">В списке расположений отключить расположения **учетных записей OneDrive** и **электронной почты Exchange** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d4722-269">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="d4722-270">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Добавить** , в раскрывающемся списке и нажмите кнопку **метки**.</span><span class="sxs-lookup"><span data-stu-id="d4722-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="d4722-271">В области **метки** нажмите кнопку **+ Добавить**, выберите **конфиденциальных** метку, нажмите кнопку **Добавить**и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="d4722-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="d4722-272">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="d4722-273">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="d4722-274">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, нажмите кнопку **Настройка подсказки и адрес электронной почты**.</span><span class="sxs-lookup"><span data-stu-id="d4722-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="d4722-275">В области **Настройка подсказок политики и уведомления по электронной почте** нажмите кнопку **Настройка текст подсказки политики**.</span><span class="sxs-lookup"><span data-stu-id="d4722-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="d4722-276">В текстовом поле введите или вставьте в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d4722-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="d4722-p108">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="d4722-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="d4722-280">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d4722-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="d4722-281">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, снимите флажок **Блокировать людей из общего доступа и ограничить доступ к общее содержимое** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="d4722-282">В **хотите ли вы включить действия политики или тестирования сначала?** области, нажмите кнопку **Да, включить немедленно**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="d4722-283">В области **Проверьте параметры** нажмите кнопку **Создать**и затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="d4722-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="d4722-284">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="d4722-284">Here is your resulting configuration.</span></span>
  
![Защита уровня конфиденциальности для изолированного сайта группы SharePoint Online, названного "Маркетинговые кампании".](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="d4722-286">Сайт стратегической группы кампании</span><span class="sxs-lookup"><span data-stu-id="d4722-286">Company strategy team site</span></span>

<span data-ttu-id="d4722-287">Для создания изолированного SharePoint Online сайт группы на уровне конфиденциальными для стратегического компании ресурсов главного Руководители организации, выполните следующее:</span><span class="sxs-lookup"><span data-stu-id="d4722-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="d4722-p109">При необходимости, используйте браузер на локальном компьютере и войдите в портал Office 365 с помощью учетной записи глобального администратора. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d4722-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d4722-290">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d4722-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d4722-291">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="d4722-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d4722-292">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="d4722-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d4722-293">В поле **имя сайта группы**введите **стратегии компании**.</span><span class="sxs-lookup"><span data-stu-id="d4722-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="d4722-294">В поле **Описание сайта группы**укажите **сайт SharePoint для стратегии компании (конфиденциальными)**.</span><span class="sxs-lookup"><span data-stu-id="d4722-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="d4722-295">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d4722-296">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="d4722-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="d4722-297">На вкладке **стратегии компании** в браузере, в панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="d4722-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="d4722-298">В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="d4722-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="d4722-299">На новой вкладке **разрешения** в браузере нажмите кнопку **Параметры запроса доступа**.</span><span class="sxs-lookup"><span data-stu-id="d4722-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="d4722-300">В диалоговом окне **Параметры запроса доступа** снимите флажок **Разрешить участникам совместного использования сайтов и отдельных файлов и папок** и **Разрешить участникам приглашать других людей для группы участников сайта** (, чтобы все три флажка), а затем нажмите кнопку ** Кнопки ОК**.</span><span class="sxs-lookup"><span data-stu-id="d4722-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="d4722-301">Выберите **стратегии компании элементы** в списке.</span><span class="sxs-lookup"><span data-stu-id="d4722-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="d4722-302">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="d4722-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="d4722-303">В диалоговом окне **общий доступ** введите **C Suite**, выберите его и нажмите кнопку **совместный доступ**.</span><span class="sxs-lookup"><span data-stu-id="d4722-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="d4722-304">В списке выберите **стратегии компании владельцев** .</span><span class="sxs-lookup"><span data-stu-id="d4722-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="d4722-305">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="d4722-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="d4722-306">В диалоговом окне **общий доступ** введите **ИТ-специалистов**, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="d4722-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="d4722-307">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="d4722-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="d4722-308">Закройте вкладку **людей и групп** в браузере, перейдите на вкладку **Главная страница компании стратегии** в браузере, а затем закройте в области **разрешения для сайта** .</span><span class="sxs-lookup"><span data-stu-id="d4722-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="d4722-309">Ниже представлены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="d4722-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="d4722-310">**Стратегия компании — члены** группы SharePoint содержит только группы **C Suite** (который содержит только CEO, финансового Директора и директор по информационным Технологиям учетные записи пользователей) и **стратегии компании** (который содержит только учетная запись пользователя глобального администратора).</span><span class="sxs-lookup"><span data-stu-id="d4722-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="d4722-311">**Стратегия компании - владельцев** группы SharePoint содержит только группы **ИТ-специалистов** (который содержит только ITAdmin1 и ITAdmin2 учетные записи пользователей).</span><span class="sxs-lookup"><span data-stu-id="d4722-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="d4722-312">**Стратегия компании - посетители** группы SharePoint не содержит групп или учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="d4722-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="d4722-313">Члены не могут изменять разрешения на уровне сайта (это может быть выполнено только члены группы **Владельцами стратегии компании** ).</span><span class="sxs-lookup"><span data-stu-id="d4722-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="d4722-p110">Другие учетные записи пользователей не удается доступ к узлу или его ресурсов или запросить доступ к сайту. Глобальный администратор или членом группы **Стратегии компании - владельцев** , необходимо выполнить дополнительные разрешения для сайта.</span><span class="sxs-lookup"><span data-stu-id="d4722-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="d4722-316">Затем настройте папку документов на сайте стратегической группы компании на использование метки "Строго конфиденциально".</span><span class="sxs-lookup"><span data-stu-id="d4722-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="d4722-317">На вкладке **Главная страница компании стратегии** браузера щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="d4722-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d4722-318">Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="d4722-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d4722-319">В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="d4722-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d4722-320">В поле **Применить параметры метки**выберите **Конфиденциальными**и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="d4722-321">Настройте политику предотвращения потери данных, которое пользователи блоки при их совместное использование документов на сайте группы SharePoint Online с конфиденциальными метки, который включает сайта стратегии компании, за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="d4722-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="d4722-p111">В случае необходимости, используйте браузер на локальном компьютере и войдите в портал Office 365 с использованием учетной записи, имеющей роли безопасности администратора или администратора компании. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d4722-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d4722-324">На вкладке **Microsoft Office для дома** в браузере выберите **безопасности &amp; соответствия** заголовков.</span><span class="sxs-lookup"><span data-stu-id="d4722-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="d4722-325">В новом **безопасности &amp; соответствия** в браузере, щелкните **защиту от потери данных > политики**.</span><span class="sxs-lookup"><span data-stu-id="d4722-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="d4722-326">На левой панели **защиту от потери данных** нажмите кнопку **+ Создать политику**.</span><span class="sxs-lookup"><span data-stu-id="d4722-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="d4722-327">В **Начать с шаблоном или создайте пользовательскую политику** области, выберите **настраиваемые**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d4722-328">В области **Имя политики** введите **конфиденциальными метки SharePoint Online веб-сайтов групп** в поле **имя**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d4722-329">На левой панели **Выберите расположение** нажмите кнопку **выбрать определенные расположения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d4722-330">В списке расположений отключить расположения **учетных записей OneDrive** и **электронной почты Exchange** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="d4722-331">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="d4722-332">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Добавить** , в раскрывающемся списке и нажмите кнопку **метки**.</span><span class="sxs-lookup"><span data-stu-id="d4722-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="d4722-333">На левой панели **метки** нажмите кнопку **+ Добавить**, выберите метку **Конфиденциальными** , нажмите кнопку **Добавить**и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="d4722-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="d4722-334">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="d4722-335">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="d4722-336">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, нажмите кнопку **Настройка подсказки и адрес электронной почты**.</span><span class="sxs-lookup"><span data-stu-id="d4722-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="d4722-337">В области **Настройка подсказок политики и уведомления по электронной почте** нажмите кнопку **Настройка текст подсказки политики**.</span><span class="sxs-lookup"><span data-stu-id="d4722-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="d4722-338">В текстовом поле введите или вставьте в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d4722-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="d4722-p112">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="d4722-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="d4722-342">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d4722-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="d4722-343">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, выберите **Требовать деловое обоснование для переопределения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="d4722-344">В **хотите ли вы включить действия политики или тестирования сначала?** области, нажмите кнопку **Да, включить немедленно**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d4722-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="d4722-345">В области **Проверьте параметры** нажмите кнопку **Создать**и затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="d4722-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="d4722-346">Затем следуйте инструкциям в [Активировать Azure службы управления правами с помощью центра администрирования Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="d4722-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="d4722-347">Далее настройте защита информации Azure с новой областью видимости политики и вложенных метку для защиты и разрешения с помощью следующих действий:</span><span class="sxs-lookup"><span data-stu-id="d4722-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="d4722-p113">Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d4722-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d4722-350">Перейдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), открыв отдельную вкладку браузера.</span><span class="sxs-lookup"><span data-stu-id="d4722-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="d4722-351">Если вы настраиваете Azure Information Protection впервые, ознакомьтесь с этими [инструкциями](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="d4722-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="d4722-352">На панели списка выберите **Дополнительные службы**, введите **Информация**, а затем выберите **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="d4722-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="d4722-353">В колонке **Azure Information Protection**, щелкните последовательно элементы **Политики в области > + Добавить политику**.</span><span class="sxs-lookup"><span data-stu-id="d4722-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="d4722-354">В **имени политики** и **метки для документов на сайте рабочей группы стратегии компании** в **поле Описание**введите **CompanyStrategy** .</span><span class="sxs-lookup"><span data-stu-id="d4722-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="d4722-355">Нажмите кнопку **выбрать, какие пользователи или группы получить эту политику > пользователей и групп**, а затем выберите **Набор C**.</span><span class="sxs-lookup"><span data-stu-id="d4722-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="d4722-356">Щелкните элементы **Выбрать > ОК**.</span><span class="sxs-lookup"><span data-stu-id="d4722-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="d4722-357">Для метки **Строго конфиденциально** щелкните последовательно многоточие (…) и элемент **Добавить подчин. метку**.</span><span class="sxs-lookup"><span data-stu-id="d4722-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="d4722-358">Введите имя подчиненной метки в поле **Имя** и описание метки в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="d4722-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="d4722-359">В разделе **Задайте разрешения для документов и электронных писем, имеющих эту метку** нажмите кнопку **Защитить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="d4722-360">В разделе **Защита** выберите элемент **Azure (облачный ключ)**.</span><span class="sxs-lookup"><span data-stu-id="d4722-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="d4722-361">В колонке **Защита**, в разделе **Параметры защиты**, нажмите **+ Добавить разрешения**.</span><span class="sxs-lookup"><span data-stu-id="d4722-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="d4722-362">Перейдите к колонке **Добавление разрешений** и выберите **+ Обзор каталога** в разделе **Укажите пользователей и группы**.</span><span class="sxs-lookup"><span data-stu-id="d4722-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="d4722-363">В области **AAD пользователей и групп** выберите **Набор C**и нажмите кнопку **выбрать**.</span><span class="sxs-lookup"><span data-stu-id="d4722-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="d4722-364">В разделе **Выбор разрешений из шаблона** снимите флажки **Печать**, **Копирование и извлечение контента** и **Переадресация**.</span><span class="sxs-lookup"><span data-stu-id="d4722-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="d4722-365">Дважды нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d4722-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="d4722-366">В колонке **Подчиненная метка** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="d4722-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="d4722-367">Закройте колонку новой политики области.</span><span class="sxs-lookup"><span data-stu-id="d4722-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="d4722-368">На blade **Защита информации Azure - областью видимости политик** нажмите кнопку **Опубликовать**и нажмите кнопку **Да**.</span><span class="sxs-lookup"><span data-stu-id="d4722-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="d4722-369">Чтобы защитить документ с Azure защита информации и этой новой метки, необходимо [установить клиент защита информации Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) на тестовом компьютере, установка Office с портала Office 365 и войдите в из Microsoft Word с использованием учетной записи в ** C-Suite** группы пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="d4722-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="d4722-370">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="d4722-370">Here is your resulting configuration.</span></span>
  
![Защита уровня строгой конфиденциальности для изолированного сайта группы SharePoint Online, названного "Стратегия компании".](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="d4722-372">Теперь все готово для создания документов на эти четыре сайтах и тестирования доступа к ним с помощью различных учетных записей пользователей в пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="d4722-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="d4722-373">Вот общей конфигурации для четырех SharePoint Online сайтов групп.</span><span class="sxs-lookup"><span data-stu-id="d4722-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Все четыре сайта группы в безопасной среде разработки и тестирования SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="d4722-375">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="d4722-375">Next step</span></span>

<span data-ttu-id="d4722-376">Если все готово для производственного развертывания безопасных сайтами SharePoint Online, видеть [безопасной SharePoint Online сайтами и файлами](secure-sharepoint-online-sites-and-files.md) подробные сведения и ссылки на статьи о развертывании пошаговые.</span><span class="sxs-lookup"><span data-stu-id="d4722-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d4722-377">See Also</span><span class="sxs-lookup"><span data-stu-id="d4722-377">See Also</span></span>

[<span data-ttu-id="d4722-378">Безопасность сайтов и файлов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d4722-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="d4722-379">Решения для обеспечения безопасности</span><span class="sxs-lookup"><span data-stu-id="d4722-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="d4722-380">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="d4722-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="d4722-381">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="d4722-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




