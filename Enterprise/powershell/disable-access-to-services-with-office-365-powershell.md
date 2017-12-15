---
title: "Отключение доступа к службам с помощью Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "В данной статье описывается использование Office 365 PowerShell для добавления или удаления доступа к службам Office 365 для пользователей в вашей организации."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="301aa-103">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="301aa-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="301aa-104">**Сводка:** В данной статье описывается использование Office 365 PowerShell для добавления или удаления доступа к службам Office 365 для пользователей в вашей организации.</span><span class="sxs-lookup"><span data-stu-id="301aa-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="301aa-p101">Если учетная запись Office 365 назначена лицензия из плана лицензирования, служб Office 365 становятся доступными для пользователя из этой лицензии. Тем не менее можно управлять служб Office 365, которые могут иметь доступ этот пользователь. Например несмотря на то, что лицензия позволяет получить доступ к SharePoint Online, можно отключить доступ к нему. На самом деле Office 365 PowerShell можно использовать для отключения доступа к любой номер для служб:</span><span class="sxs-lookup"><span data-stu-id="301aa-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="301aa-109">отдельная учетная запись;</span><span class="sxs-lookup"><span data-stu-id="301aa-109">An individual account.</span></span>
    
- <span data-ttu-id="301aa-110">группа учетных записей;</span><span class="sxs-lookup"><span data-stu-id="301aa-110">A group of accounts.</span></span>
    
- <span data-ttu-id="301aa-111">все учетные записи в организации.</span><span class="sxs-lookup"><span data-stu-id="301aa-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="301aa-112">**Содержимое:** [Краткого (инструкции без объяснения)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [Длинные версии (инструкции с подробными пояснениями)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [См. также:](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="301aa-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="301aa-113">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="301aa-113">Before you begin</span></span>
<span data-ttu-id="301aa-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="301aa-114"></span></span>

- <span data-ttu-id="301aa-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="301aa-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="301aa-p103">Командлет **Get-MsolAccountSku** используется для просмотра доступные планы лицензирования и служб Office 365, доступные в этих планах. Для получения дополнительных сведений см.[Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="301aa-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="301aa-119">Чтобы просмотреть до и после выполнения процедур, описанных в данном разделе увидеть [просмотреть сведения о лицензии и службы учетной записи с помощью Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="301aa-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="301aa-p104">Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="301aa-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="301aa-123">Если использовать командлет **Get-MsolUser** без параметра _All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="301aa-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="301aa-124">Краткая версия (инструкции без пояснений)</span><span class="sxs-lookup"><span data-stu-id="301aa-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="301aa-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="301aa-125"></span></span>

<span data-ttu-id="301aa-p105">В этом разделе процедуры представлены без лишних слов и объяснений. Если у вас возникнут вопросы или вам потребуются дополнительные сведения, вы можете прочитать остальные разделы статьи.</span><span class="sxs-lookup"><span data-stu-id="301aa-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="301aa-128">Чтобы отключить служб Office 365 для пользователей из одного плана лицензирования, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="301aa-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="301aa-129">Выбор нежелательный служб в плане лицензирования, используя следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="301aa-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="301aa-130">В этом примере создается объект **LicenseOptions** , который отключает службы Office Online и SharePoint Online в плане лицензирования с именем `litwareinc:ENTERPRISEPACK` (Office 365 для предприятий E3).</span><span class="sxs-lookup"><span data-stu-id="301aa-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="301aa-131">Используйте объект **LicenseOptions** из шага 1 на одного или нескольких пользователей.</span><span class="sxs-lookup"><span data-stu-id="301aa-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="301aa-132">Чтобы создать учетную запись, для которой отключены службы, используйте указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="301aa-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="301aa-133">В этом примере показано, как создать учетную запись для пользователя Allie Bellew, назначить лицензию и отключить службы, описанные в действии 1.</span><span class="sxs-lookup"><span data-stu-id="301aa-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="301aa-134">Дополнительные сведения о создании учетных записей пользователей в Office 365 PowerShell можно [Создать учетные записи пользователей с Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="301aa-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="301aa-135">Чтобы отключить службы для существующего лицензированного пользователя, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="301aa-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="301aa-136">В этом примере показано, как отключить службы для пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="301aa-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="301aa-137">Для отключения служб, описанных в разделе шаг 1 для всех существующих лицензированных пользователей, укажите имя плана Office 365 с экрана в командлет **Get-MsolAccountSku** (например, **litwareinc: enterprisepack** ) и затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="301aa-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="301aa-138">Чтобы отключить службы для группы существующих пользователей, воспользуйтесь одним из указанных ниже методов для идентификации пользователей.</span><span class="sxs-lookup"><span data-stu-id="301aa-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="301aa-139">**Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="301aa-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="301aa-140">В этом примере показано, как отключить службы для пользователей из отдела продаж в США.</span><span class="sxs-lookup"><span data-stu-id="301aa-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="301aa-141">**Использование списка определенных учетных записей** Для этого выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="301aa-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="301aa-142">Создайте текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="301aa-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="301aa-143">В этом примере в текстовом файле — C:\\Мои документы\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="301aa-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="301aa-144">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="301aa-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="301aa-145">Для отключения служб Office 365 для пользователей во время при назначении их план лицензирования см [запрещать доступ к службам при назначении лицензии пользователя](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="301aa-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="301aa-146">Чтобы отключить служб Office 365 для пользователей в все доступные планы лицензирования, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="301aa-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="301aa-147">Скопируйте и вставьте сценарий в Блокнот.</span><span class="sxs-lookup"><span data-stu-id="301aa-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="301aa-148">В своей среде настройте указанные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="301aa-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="301aa-149">_<UndesirableService>_В этом примере мы будем использовать Office Online и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="301aa-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="301aa-150">_<Account>_В этом примере мы будем использовать belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="301aa-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="301aa-151">Измененный сценарий выглядит указанным ниже образом.</span><span class="sxs-lookup"><span data-stu-id="301aa-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="301aa-p106">Сохраните сценарий в `RemoveO365Services.ps1` в папке, где можно найти. В данном примере мы будем сохраните файл в " `C:\\O365 Scripts`«.</span><span class="sxs-lookup"><span data-stu-id="301aa-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="301aa-154">Запустите сценарий в Office 365 PowerShell с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="301aa-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="301aa-155">Для отмены эффекты любого из этих процедур (то есть, чтобы повторно включить отключенные службы), снова выполнить процедуру, но использовать значение `$null` для параметра _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="301aa-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="301aa-156">В начало</span><span class="sxs-lookup"><span data-stu-id="301aa-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="301aa-157">Подробная версия (инструкции с подробными пояснениями)</span><span class="sxs-lookup"><span data-stu-id="301aa-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="301aa-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="301aa-158"></span></span>

<span data-ttu-id="301aa-p107">По умолчанию все службы включены при использовании функции лицензии с помощью Office 365 PowerShell. И часто это хорошо: это означает, что вы можете быстро и легко назначение лицензий пользователям без указания включения каждой службы по пути.</span><span class="sxs-lookup"><span data-stu-id="301aa-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="301aa-p108">Другой стороны, который, тем не менее, верно, кроме того, можно ограничить список доступных служб некоторым пользователям; Например может быть некоторые пользователи должны иметь доступ к Office профессиональный плюс, Скайп для бизнеса в Интернет и Exchange Online, но те же пользователи не следует иметь доступ к SharePoint Online или Office Online. Можно ограничить учетных записей, образом? Как оказывается, вы можете. Чтобы объяснить, как это работает, давайте два подхода к решению этой проблемы:</span><span class="sxs-lookup"><span data-stu-id="301aa-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="301aa-165">Назначение пользователю лицензии Office 365, которая автоматически включает все службы.</span><span class="sxs-lookup"><span data-stu-id="301aa-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="301aa-166">Выполнение пары команд Office 365 PowerShell, отключающих указанные службы для этого пользователя.</span><span class="sxs-lookup"><span data-stu-id="301aa-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="301aa-p109">Мы проведена шаг 1: наших пользователей (Светлане Коноваловой) имеет лицензии Office 365, который предоставляет ему с доступом к службам Office 365. Тем не менее, его нужно изменить учетную запись Светлане таким образом, чтобы она не имеет доступа к SharePoint Online ( `SHAREPOINTENTERPRISE`) или на узле Office Online ( `SHAREPOINTWAC`). Но как мы должны сделать это?</span><span class="sxs-lookup"><span data-stu-id="301aa-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="301aa-p110">Вот как. Начинается с мы будем использовать командлет **New-MsolLicenseOptions** для создания объекта **LicenseOption** , который содержит службы, которые необходимо отключить. В случае Светлане его нужно отключить `SHAREPOINTENTERPRISE` и `SHAREPOINTWAC`, поэтому мы используем эту команду:</span><span class="sxs-lookup"><span data-stu-id="301aa-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="301aa-p111">Видите, как это работает? Вы задаете план лицензирования ( `litwareinc:ENTERPRISEPACK`) и затем указываете каждую из служб, которые нужно отключить, разделяя их запятыми.</span><span class="sxs-lookup"><span data-stu-id="301aa-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="301aa-p112">Убедитесь, что ваш новый объект **LicenseOption** сохранить в переменной. В предыдущем примере мы использовали `$x`, хотя можно использовать любое допустимое имя переменной Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="301aa-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="301aa-177">На этом этапе можно использовать следующую команду для отключения Светлане доступ две службы:</span><span class="sxs-lookup"><span data-stu-id="301aa-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="301aa-p113">Ничего не слишком фигурном здесь, либо: мы просто вызовите командлет **Set-MsolUserLicense** и включить параметр _LicenseOptions_ , а также переменной ( `$x`) содержащий планов, его нужно отключить. И что мы видим теперь Если взглянуть на информацию о лицензии Светлане, выполнив команду: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Мы увидеть следующее:</span><span class="sxs-lookup"><span data-stu-id="301aa-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="301aa-p114">Здорово, правда? И, конечно, то же самое можно делать к нескольким пользователям при желании. Например эти команды отключить же две службы для всех наших лицензированных пользователей. Укажите имя плана Office 365 с экрана в командлет **Get-MsolAccountSku** (например, **litwareinc: enterprisepack** ) и затем использовать их для работы.</span><span class="sxs-lookup"><span data-stu-id="301aa-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="301aa-p115">Помните, что Светлане по-прежнему имеет действительной лицензии Office 365; он является теперь у нее есть доступ к службам меньшего числа. Прежде чем мы отключили две службы, Светлане имел доступ к каналы новостей, OneDrive и SharePoint Online сайтов:</span><span class="sxs-lookup"><span data-stu-id="301aa-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![Пользователь с доступом к SharePoint.](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="301aa-188">Теперь эти возможности ей недоступны.</span><span class="sxs-lookup"><span data-stu-id="301aa-188">Now those options are no longer available to her:</span></span>
  
![Пользователь без доступа к SharePoint.](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="301aa-190">Мы хотели сделать именно это.</span><span class="sxs-lookup"><span data-stu-id="301aa-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="301aa-p116">И что делать, если мы наших виду впоследствии изменить: можно ли включить данные службы? Вы уверены, что Да. Чтобы повторно включить все службы для пользователя, используйте следующую команду для создания следующих объектов **LicenseOption** :</span><span class="sxs-lookup"><span data-stu-id="301aa-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="301aa-p117">Что такое этой команды? Чтобы начать с помощью Windows PowerShell константу `$null` означает, что «нет». (Или немного больше технические языке, это означает «нулевое значение».) Как вы помните, когда мы используем командлет **New-MsolLicenseOptions** , у нас есть укажите службы, мы должны отключено. В этом случае мы не должен любую из служб, чтобы отключить. Вы уверены, что мы могли бы использовать команду следующим образом, где мы не задано значение для параметра _DisabledPlans_ команду, которая может быть:</span><span class="sxs-lookup"><span data-stu-id="301aa-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="301aa-p118">Тем не менее, которые не будут работать. Вместо этого он создает сообщение об ошибке:</span><span class="sxs-lookup"><span data-stu-id="301aa-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="301aa-201">К счастью для нас, установка для параметра значения `$null` работы:</span><span class="sxs-lookup"><span data-stu-id="301aa-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="301aa-202">Это просто значит, что при выполнении командлета **Set-MsolUserLicense** мы указываем **Set-MsolUserLicense** , что мы не на какие-либо отключенные службы.</span><span class="sxs-lookup"><span data-stu-id="301aa-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="301aa-203">Само собой понятно, что если ни одна из служб не отключена, то все службы включены.</span><span class="sxs-lookup"><span data-stu-id="301aa-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="301aa-p119">Теперь, когда вы понимаете, как это работает, давайте показано, как выдавать лицензии и отключение указанных служб и всех с помощью одной команды. Звучит довольно Впечатляет, но честно, в этом нет ничего не к нему: только что включают _Параметры AddLicenses_ и _LicenseOptions_ используются в одной команде. Другими словами сначала создайте объект **LicenseOption** :</span><span class="sxs-lookup"><span data-stu-id="301aa-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="301aa-207">И затем, как указывалось ранее, использовать _Параметры AddLicenses_ и _LicenseOptions_ используются в команде:</span><span class="sxs-lookup"><span data-stu-id="301aa-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="301aa-208">Что команда будет выдавать Светлане Коноваловой новую лицензию, но лицензии в какие Скайп для бизнеса в Интернет ( `SHAREPOINTWAC`) и SharePoint Online ( `SHAREPOINTENTERPRISE`) являются оба отключены.</span><span class="sxs-lookup"><span data-stu-id="301aa-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="301aa-209">В начало</span><span class="sxs-lookup"><span data-stu-id="301aa-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="301aa-210">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="301aa-210">New to Office 365?</span></span>
<span data-ttu-id="301aa-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="301aa-211"></span></span>

||
|:-----|
|<span data-ttu-id="301aa-p120">![Короткие значок обучения LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Создать в Office 365?**         Обнаружение Бесплатные курсы видео для **ИТ-специалистов и администраторов Office 365**, с LinkedIn обучения.</span><span class="sxs-lookup"><span data-stu-id="301aa-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="301aa-214">See also</span><span class="sxs-lookup"><span data-stu-id="301aa-214">See also</span></span>
<span data-ttu-id="301aa-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="301aa-215"></span></span>

<span data-ttu-id="301aa-216">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="301aa-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="301aa-217">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="301aa-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="301aa-218">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="301aa-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="301aa-219">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="301aa-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="301aa-220">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="301aa-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="301aa-221">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="301aa-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="301aa-222">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="301aa-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="301aa-223">Get-Content</span><span class="sxs-lookup"><span data-stu-id="301aa-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="301aa-224">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="301aa-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="301aa-225">Новый MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="301aa-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="301aa-226">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="301aa-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="301aa-227">Новый MsolUser</span><span class="sxs-lookup"><span data-stu-id="301aa-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="301aa-228">SET-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="301aa-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="301aa-229">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="301aa-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="301aa-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="301aa-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="301aa-231">В начало</span><span class="sxs-lookup"><span data-stu-id="301aa-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

