---
title: Отключение доступа к службам во время назначения лицензий
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Сведения о том, как назначать лицензии для учетных записей пользователей и отключать определенные планы обслуживания, используя PowerShell в Office 365.
ms.openlocfilehash: f45c76ba0e756aec057e4243ece51de2af26aaec
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782149"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="7d7fb-103">Отключение доступа к службам во время назначения лицензий</span><span class="sxs-lookup"><span data-stu-id="7d7fb-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="7d7fb-104">**Сводка.** Узнайте, как назначать лицензии пользователям и одновременно отключать определенные планы обслуживания, используя PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="7d7fb-p101">Подписки на Office 365 включают в себя планы обслуживания для отдельных служб. Администраторам Office 365 часто нужно отключать определенные планы при назначении лицензий для пользователей. Следуя инструкциям в этой статье, вы можете с помощью PowerShell назначить лицензию на Office 365 для одной или нескольких учетных записей пользователей, при этом отключив определенные планы обслуживания.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>


## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7d7fb-108">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d7fb-108">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7d7fb-109">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="7d7fb-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="7d7fb-110">Затем выполните следующую команду, чтобы просмотреть текущие подписки:</span><span class="sxs-lookup"><span data-stu-id="7d7fb-110">Next, run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="7d7fb-111">Значение составляющих команды  `Get-MsolAccountSku`:</span><span class="sxs-lookup"><span data-stu-id="7d7fb-111">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="7d7fb-p102">**AccountSkuId** — это подписка вашей организации в формате \<НазваниеОрганизации>:\<Подписка>. \<НазваниеОрганизации> — значение, которое вы указали при регистрации в Office 365 (уникальное для организации). \<Подписка> — значение, обозначающее конкретную подписку. Например, в случае litwareinc:ENTERPRISEPACK название организации — litwareinc, а название подписки — ENTERPRISEPACK (Office 365 корпоративный E3).</span><span class="sxs-lookup"><span data-stu-id="7d7fb-p102">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="7d7fb-116">**ActiveUnits**  количество лицензий, которые вы приобрели для подписки.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-116">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="7d7fb-117">**WarningUnits** — количество лицензий для не продленной подписки, срок действия которой истекает через 30 дней льготного периода.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-117">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="7d7fb-118">**ConsumedUnits**  количество лицензий, которые вы назначили пользователям для подписки.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-118">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="7d7fb-p103">Укажите AccountSkuId для подписки на Office 365, где обозначены пользователи, которым вы хотите назначить лицензию. Убедитесь, что лицензий для назначения достаточно (отнимите **ConsumedUnits** от **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="7d7fb-p103">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="7d7fb-121">Затем выполните эту команду, чтобы просмотреть сведения о планах обслуживания Office 365, доступных для каждой из ваших подписок:</span><span class="sxs-lookup"><span data-stu-id="7d7fb-121">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="7d7fb-122">Просмотрите результаты команды и определите, какие планы обслуживания нужно отключить при назначении лицензий пользователям.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-122">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="7d7fb-123">Ниже приведен неполный список планов обслуживания и соответствующих им служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-123">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="7d7fb-124">В следующей таблице показаны планы обслуживания Office 365 и их понятные имена для наиболее распространенных служб.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-124">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="7d7fb-125">Ваш список планов обслуживания может отличаться.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-125">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="7d7fb-126">**План обслуживания**</span><span class="sxs-lookup"><span data-stu-id="7d7fb-126">**Service plan**</span></span>|<span data-ttu-id="7d7fb-127">**Описание**</span><span class="sxs-lookup"><span data-stu-id="7d7fb-127">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="7d7fb-128">Sway</span><span class="sxs-lookup"><span data-stu-id="7d7fb-128">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="7d7fb-129">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7d7fb-129">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="7d7fb-130">Yammer</span><span class="sxs-lookup"><span data-stu-id="7d7fb-130">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="7d7fb-131">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="7d7fb-131">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="7d7fb-132">Office профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="7d7fb-132">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="7d7fb-133">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="7d7fb-133">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="7d7fb-134">Office</span><span class="sxs-lookup"><span data-stu-id="7d7fb-134">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="7d7fb-135">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7d7fb-135">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="7d7fb-136">Exchange Online (план 2)</span><span class="sxs-lookup"><span data-stu-id="7d7fb-136">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="7d7fb-137">Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="7d7fb-137">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="7d7fb-138">Теперь, когда у вас есть AccountSkuId и планы обслуживания, которые нужно отключить, вы можете назначить лицензии для одного или нескольких пользователей.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-138">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="7d7fb-139">Для одного пользователя</span><span class="sxs-lookup"><span data-stu-id="7d7fb-139">For a single user</span></span>

<span data-ttu-id="7d7fb-p105">Введите имя участника-пользователя из учетной записи пользователя, AccountSkuId и список отключаемых планов обслуживания, удалив при этом пояснительный текст и символы \< и >. После этого выполните полученные команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="7d7fb-142">Ниже приведен пример блока команд для учетной записи belindan@contoso.com. В этом случае указана лицензия contoso:ENTERPRISEPACK, а отключить нужно планы обслуживания RMS_S_ENTERPRISE, SWAY, INTUNE_O365 и YAMMER_ENTERPRISE.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-142">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

### <a name="for-multiple-users"></a><span data-ttu-id="7d7fb-143">Для нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="7d7fb-143">For multiple users</span></span>

<span data-ttu-id="7d7fb-p106">Чтобы выполнить эту задачу администрирования для нескольких пользователей, создайте текстовый файл с разделителями-запятыми (CSV-файл), содержащий поля UserPrincipalName и UsageLocation. Пример:</span><span class="sxs-lookup"><span data-stu-id="7d7fb-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="7d7fb-146">После этого укажите расположение входного и выходного CSV-файлов, ИД SKU учетной записи и список планов обслуживания, которые нужно отключить. Затем выполните полученные команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-146">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="7d7fb-147">Что делает этот блок команд PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7d7fb-147">This PowerShell command block:</span></span>
  
- <span data-ttu-id="7d7fb-148">Отображает имя участника-пользователя для каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-148">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="7d7fb-149">Назначает настраиваемые лицензии для каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-149">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="7d7fb-150">Создает CSV-файл со всеми обработанными пользователями и отображает состояние их лицензий.</span><span class="sxs-lookup"><span data-stu-id="7d7fb-150">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="7d7fb-151">См. также</span><span class="sxs-lookup"><span data-stu-id="7d7fb-151">See also</span></span>

[<span data-ttu-id="7d7fb-152">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d7fb-152">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="7d7fb-153">Отключение доступа к Sway с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="7d7fb-153">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="7d7fb-154">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d7fb-154">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="7d7fb-155">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="7d7fb-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

