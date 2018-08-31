---
title: Отключение доступа к службам с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/20/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Объясняет, как использовать Office 365 PowerShell для отключения доступа к службам Office 365 для пользователей в вашей организации.
ms.openlocfilehash: d65308746ac5c2b60f4749588455fa66471069e3
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914994"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="bd097-103">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd097-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="bd097-104">**Сводка:** Объясняет, как использовать Office 365 PowerShell для отключения доступа к службам Office 365 для пользователей в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="bd097-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="bd097-p101">Если учетная запись Office 365 назначена лицензия из плана лицензирования, служб Office 365 становятся доступными для пользователя из этой лицензии. Тем не менее можно управлять служб Office 365, которые могут иметь доступ этот пользователь. Например несмотря на то, что лицензия позволяет получить доступ к службе SharePoint Online, можно отключить доступ к нему. Office 365 PowerShell можно использовать для отключения доступа к любой номер для определенного плана лицензирования для служб:</span><span class="sxs-lookup"><span data-stu-id="bd097-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to the SharePoint Online service, you can disable access to it. You can use Office 365 PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="bd097-109">отдельная учетная запись;</span><span class="sxs-lookup"><span data-stu-id="bd097-109">An individual account.</span></span>
    
- <span data-ttu-id="bd097-110">группа учетных записей;</span><span class="sxs-lookup"><span data-stu-id="bd097-110">A group of accounts.</span></span>
    
- <span data-ttu-id="bd097-111">все учетные записи в организации.</span><span class="sxs-lookup"><span data-stu-id="bd097-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="bd097-112">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="bd097-112">Before you begin</span></span>
<span data-ttu-id="bd097-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="bd097-113"></span></span>

- <span data-ttu-id="bd097-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bd097-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="bd097-p103">Командлет **Get-MsolAccountSku** используется для просмотра доступные планы лицензирования и служб Office 365, доступные в этих планах. Для получения дополнительных сведений см. [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bd097-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="bd097-118">Чтобы просмотреть до и после выполнения процедур, описанных в данном разделе увидеть [просмотреть сведения о лицензии и службы учетной записи с помощью Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bd097-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="bd097-p104">Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bd097-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="bd097-122">При использовании командлета **Get-MsolUser** без использования _всех_ параметров возвращаются только первой 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="bd097-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="bd097-123">Отключение конкретных служб Office 365 для конкретных пользователей для определенного плана лицензирования</span><span class="sxs-lookup"><span data-stu-id="bd097-123">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="bd097-124">Чтобы отключить определенного набора служб Office 365 для пользователей для определенного плана лицензирования, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="bd097-124">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="bd097-125">Выбор нежелательный служб в плане лицензирования, используя следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="bd097-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="bd097-126">В следующем примере создается объект **LicenseOptions** , который отключает службы Office Online и SharePoint Online в плане лицензирования с именем `litwareinc:ENTERPRISEPACK` (Office 365 для предприятий E3).</span><span class="sxs-lookup"><span data-stu-id="bd097-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="bd097-127">Используйте объект **LicenseOptions** из действия 1 для одного или нескольких пользователей.</span><span class="sxs-lookup"><span data-stu-id="bd097-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="bd097-128">Чтобы создать учетную запись, для которой отключены службы, используйте указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="bd097-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="bd097-129">В следующем примере создается новая учетная запись для Allie Bellew, который назначает лицензии и отключает служб, описанных в шаге 1.</span><span class="sxs-lookup"><span data-stu-id="bd097-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="bd097-130">Дополнительные сведения о создании учетных записей пользователей в Office 365 PowerShell можно [Создать учетные записи пользователей с Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bd097-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="bd097-131">Чтобы отключить службы для существующего лицензированного пользователя, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="bd097-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="bd097-132">В этом примере показано, как отключить службы для пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="bd097-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="bd097-133">Для отключения служб, описанных в разделе шаг 1 для всех существующих лицензированных пользователей, укажите имя плана Office 365 с экрана в командлет **Get-MsolAccountSku** (например, **litwareinc: enterprisepack**) и затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="bd097-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="bd097-134">Чтобы отключить службы для группы существующих пользователей, воспользуйтесь одним из указанных ниже методов для идентификации пользователей.</span><span class="sxs-lookup"><span data-stu-id="bd097-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="bd097-135">**Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="bd097-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="bd097-136">В следующем примере отключается службы для сотрудников отдела продаж в США.</span><span class="sxs-lookup"><span data-stu-id="bd097-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="bd097-137">**Использование списка определенных учетных записей** Для этого выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="bd097-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="bd097-138">Создайте текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="bd097-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="bd097-139">В этом примере в текстовом файле — C:\\Мои документы\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="bd097-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="bd097-140">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="bd097-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="bd097-141">Если вы хотите отключить доступ к службам для нескольких планы лицензирования, выполните инструкции, приведенные выше для каждого плана лицензирования проверка того, что:</span><span class="sxs-lookup"><span data-stu-id="bd097-141">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="bd097-142">Учетные записи пользователей, назначенных план лицензирования.</span><span class="sxs-lookup"><span data-stu-id="bd097-142">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="bd097-143">Службы для отключения доступны в плане лицензирования.</span><span class="sxs-lookup"><span data-stu-id="bd097-143">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="bd097-144">Для отключения служб Office 365 для пользователей во время при назначении их план лицензирования см [запрещать доступ к службам при назначении лицензии пользователя](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="bd097-144">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="bd097-145">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="bd097-145">New to Office 365?</span></span>
<span data-ttu-id="bd097-146"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="bd097-146"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="bd097-147">См. также</span><span class="sxs-lookup"><span data-stu-id="bd097-147">See also</span></span>
<span data-ttu-id="bd097-148"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="bd097-148"></span></span>

<span data-ttu-id="bd097-149">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="bd097-149">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="bd097-150">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="bd097-150">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="bd097-151">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="bd097-151">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="bd097-152">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="bd097-152">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="bd097-153">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="bd097-153">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="bd097-154">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="bd097-154">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="bd097-155">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="bd097-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="bd097-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="bd097-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="bd097-157">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="bd097-157">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="bd097-158">Новый MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="bd097-158">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="bd097-159">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="bd097-159">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="bd097-160">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="bd097-160">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="bd097-161">SET-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="bd097-161">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="bd097-162">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="bd097-162">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="bd097-163">Where-Object</span><span class="sxs-lookup"><span data-stu-id="bd097-163">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

