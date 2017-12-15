---
title: "Отключение доступа к службам во время назначения лицензий"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "Сведения о том, как назначать лицензии для учетных записей пользователей и отключать определенные планы обслуживания, используя PowerShell в Office 365."
ms.openlocfilehash: 907314e13b353e5d5ddbcd8fe467db568473d0b3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="99289-103">Отключение доступа к службам во время назначения лицензий</span><span class="sxs-lookup"><span data-stu-id="99289-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="99289-104">**Сводка:**  Узнайте, как назначение лицензий для учетных записей пользователей и отключение планов обслуживания, определенных в то же время, с помощью Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99289-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="99289-p101">Подписки на Office 365 включают в себя планы обслуживания для отдельных служб. Администраторам Office 365 часто нужно отключать определенные планы при назначении лицензий для пользователей. Следуя инструкциям в этой статье, вы можете с помощью PowerShell назначить лицензию на Office 365 для одной или нескольких учетных записей пользователей, при этом отключив определенные планы обслуживания.</span><span class="sxs-lookup"><span data-stu-id="99289-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="99289-108">В основе этой статьи лежит работа Siddhartha Parmar, специалиста технической поддержки Майкрософт, занимающегося эскалированными запросами на обслуживание.</span><span class="sxs-lookup"><span data-stu-id="99289-108">This article is based on the work of Siddhartha Parmar, a Microsoft Support Escalation Engineer.</span></span> 
  
## <a name="before-you-begin"></a><span data-ttu-id="99289-109">Приступая к работе</span><span class="sxs-lookup"><span data-stu-id="99289-109">Before you begin</span></span>

<span data-ttu-id="99289-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="99289-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="99289-112">Соберите сведения о подписках и планах обслуживания</span><span class="sxs-lookup"><span data-stu-id="99289-112">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="99289-113">Выполните эту команду, чтобы увидеть текущие подписки:</span><span class="sxs-lookup"><span data-stu-id="99289-113">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="99289-114">Значение составляющих команды  `Get-MsolAccountSku`:</span><span class="sxs-lookup"><span data-stu-id="99289-114">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="99289-p103">**Включает параметры AccountSkuId** является подписки для вашей организации в \<OrganizationName >:\<подписки > формат. \<OrganizationName > — это значение, что и при участвуют в Office 365 и является уникальным для вашей организации. \<Подписки > значение предназначено для конкретной подписки. Например для litwareinc: enterprisepack, litwareinc — это название организации и ENTERPRISEPACK (Office 365 для предприятий E3) — это имя подписки.</span><span class="sxs-lookup"><span data-stu-id="99289-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="99289-119">**ActiveUnits**  количество лицензий, которые вы приобрели для подписки.</span><span class="sxs-lookup"><span data-stu-id="99289-119">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="99289-120">**WarningUnits**  количество лицензий для не продленной подписки, срок действия которой истекает через 30 дней льготного периода.</span><span class="sxs-lookup"><span data-stu-id="99289-120">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="99289-121">**ConsumedUnits**  количество лицензий, которые вы назначили пользователям для подписки.</span><span class="sxs-lookup"><span data-stu-id="99289-121">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="99289-p104">Укажите AccountSkuId для подписки на Office 365, где обозначены пользователи, которым вы хотите назначить лицензию. Убедитесь, что лицензий для назначения достаточно (отнимите **ConsumedUnits** от **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="99289-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="99289-124">Затем выполните эту команду, чтобы просмотреть сведения о планах обслуживания Office 365, доступных для каждой из ваших подписок:</span><span class="sxs-lookup"><span data-stu-id="99289-124">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="99289-125">Просмотрите результаты команды и определите, какие планы обслуживания нужно отключить при назначении лицензий пользователям.</span><span class="sxs-lookup"><span data-stu-id="99289-125">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="99289-126">Ниже приведен неполный список планов обслуживания и соответствующих им служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="99289-126">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="99289-127">**План обслуживания**</span><span class="sxs-lookup"><span data-stu-id="99289-127">**Service plan**</span></span>|<span data-ttu-id="99289-128">**Описание**</span><span class="sxs-lookup"><span data-stu-id="99289-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="99289-129">SWAY</span><span class="sxs-lookup"><span data-stu-id="99289-129">SWAY</span></span>  <br/> |<span data-ttu-id="99289-130">Sway</span><span class="sxs-lookup"><span data-stu-id="99289-130">Sway</span></span>  <br/> |
|<span data-ttu-id="99289-131">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="99289-131">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="99289-132">Управление мобильными устройствами для Office 365</span><span class="sxs-lookup"><span data-stu-id="99289-132">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="99289-133">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="99289-133">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="99289-134">Yammer</span><span class="sxs-lookup"><span data-stu-id="99289-134">Yammer</span></span>  <br/> |
|<span data-ttu-id="99289-135">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="99289-135">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="99289-136">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="99289-136">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="99289-137">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="99289-137">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="99289-138">Office профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="99289-138">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="99289-139">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="99289-139">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="99289-140">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="99289-140">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="99289-141">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="99289-141">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="99289-142">Office Online</span><span class="sxs-lookup"><span data-stu-id="99289-142">Office Online</span></span>  <br/> |
|<span data-ttu-id="99289-143">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="99289-143">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="99289-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="99289-144">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="99289-145">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="99289-145">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="99289-146">Exchange Online (план 2)</span><span class="sxs-lookup"><span data-stu-id="99289-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="99289-147">Теперь, когда у вас есть AccountSkuId и планы обслуживания, которые нужно отключить, вы можете назначить лицензии для одного или нескольких пользователей.</span><span class="sxs-lookup"><span data-stu-id="99289-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="99289-148">Для одного пользователя</span><span class="sxs-lookup"><span data-stu-id="99289-148">For a single user</span></span>

<span data-ttu-id="99289-p105">Для одного пользователя, заполните поля в имя участника-пользователя учетной записи пользователя, AccountSkuId и список планов обслуживания для отключения и удаления пояснительным текстом и \< и > символов. Выполните результирующий команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99289-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="99289-151">Ниже приведен пример блока команд для учетной записи belindan@contoso.com. В этом случае указана лицензия contoso:ENTERPRISEPACK, а отключить нужно планы обслуживания RMS_S_ENTERPRISE, SWAY, INTUNE_O365 и YAMMER_ENTERPRISE.</span><span class="sxs-lookup"><span data-stu-id="99289-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
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

## <a name="for-multiple-users"></a><span data-ttu-id="99289-152">Для нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="99289-152">For multiple users</span></span>

<span data-ttu-id="99289-p106">Чтобы выполнить эту задачу администрирования для нескольких пользователей, создайте текстовый файл с разделителями-запятыми (CSV-файл), содержащий поля UserPrincipalName и UsageLocation. Пример:</span><span class="sxs-lookup"><span data-stu-id="99289-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="99289-155">После этого укажите расположение входного и выходного CSV-файлов, ИД SKU учетной записи и список планов обслуживания, которые нужно отключить. Затем выполните полученные команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99289-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="99289-156">Что делает этот блок команд PowerShell:</span><span class="sxs-lookup"><span data-stu-id="99289-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="99289-157">Отображает имя участника-пользователя для каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="99289-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="99289-158">Назначает настраиваемые лицензии для каждого пользователя.</span><span class="sxs-lookup"><span data-stu-id="99289-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="99289-159">Создает CSV-файл со всеми обработанными пользователями и отображает состояние их лицензий.</span><span class="sxs-lookup"><span data-stu-id="99289-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="99289-160">See also</span><span class="sxs-lookup"><span data-stu-id="99289-160">See also</span></span>

#### 

[<span data-ttu-id="99289-161">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="99289-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="99289-162">Отключение доступа к Sway с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="99289-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="99289-163">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="99289-163">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="99289-164">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="99289-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

