---
title: "Отключение доступа к службам с помощью Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
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
description: "Объясняет, как использовать Office 365 PowerShell для отключения доступа к службам Office 365 для пользователей в вашей организации."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="aa65e-103">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa65e-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="aa65e-104">**Сводка:** Объясняет, как использовать Office 365 PowerShell для отключения доступа к службам Office 365 для пользователей в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="aa65e-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="aa65e-p101">Если учетная запись Office 365 назначена лицензия из плана лицензирования, служб Office 365 становятся доступными для пользователя из этой лицензии. Тем не менее можно управлять служб Office 365, которые могут иметь доступ этот пользователь. Например несмотря на то, что лицензия позволяет получить доступ к SharePoint Online, можно отключить доступ к нему. На самом деле Office 365 PowerShell можно использовать для отключения доступа к любой номер для служб:</span><span class="sxs-lookup"><span data-stu-id="aa65e-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="aa65e-109">отдельная учетная запись;</span><span class="sxs-lookup"><span data-stu-id="aa65e-109">An individual account.</span></span>
    
- <span data-ttu-id="aa65e-110">группа учетных записей;</span><span class="sxs-lookup"><span data-stu-id="aa65e-110">A group of accounts.</span></span>
    
- <span data-ttu-id="aa65e-111">все учетные записи в организации.</span><span class="sxs-lookup"><span data-stu-id="aa65e-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="aa65e-112">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="aa65e-112">Before you begin</span></span>
<span data-ttu-id="aa65e-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="aa65e-113"></span></span>

- <span data-ttu-id="aa65e-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="aa65e-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="aa65e-p103">Командлет **Get-MsolAccountSku** используется для просмотра доступные планы лицензирования и служб Office 365, доступные в этих планах. Для получения дополнительных сведений см. [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="aa65e-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="aa65e-118">Чтобы просмотреть до и после выполнения процедур, описанных в данном разделе увидеть [просмотреть сведения о лицензии и службы учетной записи с помощью Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="aa65e-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="aa65e-p104">Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="aa65e-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="aa65e-122">При использовании командлета **Get-MsolUser** без использования _всех_ параметров возвращаются только первой 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="aa65e-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="aa65e-123">Планирование конкретных служб Office 365 для конкретных пользователей для одной лицензирования</span><span class="sxs-lookup"><span data-stu-id="aa65e-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="aa65e-124">Чтобы отключить определенного набора служб Office 365 для пользователей из одного плана лицензирования, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="aa65e-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="aa65e-125">Выбор нежелательный служб в плане лицензирования, используя следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="aa65e-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="aa65e-126">В следующем примере создается объект **LicenseOptions** , который отключает службы Office Online и SharePoint Online в плане лицензирования с именем `litwareinc:ENTERPRISEPACK` (Office 365 для предприятий E3).</span><span class="sxs-lookup"><span data-stu-id="aa65e-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="aa65e-127">Используйте объект **LicenseOptions** из шага 1 на одного или нескольких пользователей.</span><span class="sxs-lookup"><span data-stu-id="aa65e-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="aa65e-128">Чтобы создать учетную запись, для которой отключены службы, используйте указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="aa65e-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="aa65e-129">В следующем примере создается новая учетная запись для Allie Bellew, который назначает лицензии и отключает служб, описанных в шаге 1.</span><span class="sxs-lookup"><span data-stu-id="aa65e-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="aa65e-130">Дополнительные сведения о создании учетных записей пользователей в Office 365 PowerShell можно [Создать учетные записи пользователей с Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="aa65e-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="aa65e-131">Чтобы отключить службы для существующего лицензированного пользователя, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="aa65e-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="aa65e-132">В этом примере показано, как отключить службы для пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="aa65e-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="aa65e-133">Для отключения служб, описанных в разделе шаг 1 для всех существующих лицензированных пользователей, укажите имя плана Office 365 с экрана в командлет **Get-MsolAccountSku** (например, **litwareinc: enterprisepack**) и затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="aa65e-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="aa65e-134">Чтобы отключить службы для группы существующих пользователей, воспользуйтесь одним из указанных ниже методов для идентификации пользователей.</span><span class="sxs-lookup"><span data-stu-id="aa65e-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="aa65e-135">**Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="aa65e-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="aa65e-136">В следующем примере отключается службы для сотрудников отдела продаж в США.</span><span class="sxs-lookup"><span data-stu-id="aa65e-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="aa65e-137">**Использование списка определенных учетных записей** Для этого выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="aa65e-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="aa65e-138">Создайте текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="aa65e-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="aa65e-139">В этом примере в текстовом файле — C:\\Мои документы\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="aa65e-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="aa65e-140">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="aa65e-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="aa65e-141">Для отключения служб Office 365 для пользователей во время при назначении их план лицензирования см [запрещать доступ к службам при назначении лицензии пользователя](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="aa65e-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="aa65e-142">Конкретных служб Office 365 для пользователей из всех планы лицензирования</span><span class="sxs-lookup"><span data-stu-id="aa65e-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="aa65e-143">Чтобы отключить служб Office 365 для пользователей в все доступные планы лицензирования, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="aa65e-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="aa65e-144">Скопируйте и вставьте сценарий в Блокнот.</span><span class="sxs-lookup"><span data-stu-id="aa65e-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="aa65e-145">В своей среде настройте указанные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="aa65e-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="aa65e-146">_<UndesirableService>_В этом примере мы будем использовать Office Online и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="aa65e-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="aa65e-147">_<Account>_В этом примере мы будем использовать belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="aa65e-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="aa65e-148">Измененный сценарий выглядит указанным ниже образом.</span><span class="sxs-lookup"><span data-stu-id="aa65e-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="aa65e-p105">Сохраните сценарий в `RemoveO365Services.ps1` в папке, где можно найти. В данном примере мы будем сохраните файл в `C:\\O365 Scripts`.</span><span class="sxs-lookup"><span data-stu-id="aa65e-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="aa65e-151">Запустите сценарий в Office 365 PowerShell с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="aa65e-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="aa65e-152">Для отмены эффекты любого из этих процедур (то есть, чтобы повторно включить отключенные службы), снова выполнить процедуру, но использовать значение `$null` для параметра _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="aa65e-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="aa65e-153">В начало</span><span class="sxs-lookup"><span data-stu-id="aa65e-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a><span data-ttu-id="aa65e-154">Все службы Office 365 для всех пользователей для одного плана лицензирования</span><span class="sxs-lookup"><span data-stu-id="aa65e-154">All Office 365 services for all users for a single licensing plan</span></span>
 
<span data-ttu-id="aa65e-155">Чтобы отключить все службы Office 365 для всех пользователей в определенных плана лицензирования, укажите имя плана лицензирования для $acctSKU (например, **litwareinc: enterprisepack**) и затем выполните следующие команды в окне командной строки PowerShell:</span><span class="sxs-lookup"><span data-stu-id="aa65e-155">To disable all Office 365 services for all users in a specific licensing plan, specify the licensing plan name for $acctSKU (such as **litwareinc:ENTERPRISEPACK**), and then run these commands in the PowerShell command window:</span></span>

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a><span data-ttu-id="aa65e-156">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="aa65e-156">New to Office 365?</span></span>
<span data-ttu-id="aa65e-157"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="aa65e-157"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="aa65e-158">См. также</span><span class="sxs-lookup"><span data-stu-id="aa65e-158">See also</span></span>
<span data-ttu-id="aa65e-159"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="aa65e-159"></span></span>

<span data-ttu-id="aa65e-160">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="aa65e-160">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="aa65e-161">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="aa65e-161">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="aa65e-162">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="aa65e-162">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="aa65e-163">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="aa65e-163">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="aa65e-164">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="aa65e-164">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="aa65e-165">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="aa65e-165">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="aa65e-166">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="aa65e-166">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="aa65e-167">Get-Content</span><span class="sxs-lookup"><span data-stu-id="aa65e-167">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="aa65e-168">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="aa65e-168">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="aa65e-169">Новый MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="aa65e-169">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="aa65e-170">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="aa65e-170">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="aa65e-171">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="aa65e-171">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="aa65e-172">SET-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="aa65e-172">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="aa65e-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="aa65e-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="aa65e-174">Where-Object</span><span class="sxs-lookup"><span data-stu-id="aa65e-174">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

