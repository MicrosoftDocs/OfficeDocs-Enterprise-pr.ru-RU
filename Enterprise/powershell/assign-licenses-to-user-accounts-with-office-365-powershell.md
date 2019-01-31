---
title: Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651187"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="abfa1-103">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="abfa1-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="abfa1-104">**Сводка:**  В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.</span><span class="sxs-lookup"><span data-stu-id="abfa1-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="abfa1-p101">Пользователи не могут использовать какие-либо службы Office 365, пока не своей учетной записи будет назначена лицензия из плана лицензирования. Office 365 PowerShell позволяет быстро назначение лицензий нелицензированных учетным записям.</span><span class="sxs-lookup"><span data-stu-id="abfa1-p101">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan. You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="abfa1-107">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="abfa1-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="abfa1-108">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="abfa1-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="abfa1-109">Рассмотрим процедуру список планов лицензии для клиента с помощью этой команды.</span><span class="sxs-lookup"><span data-stu-id="abfa1-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="abfa1-110">Затем получите учетное имя учетной записи, к которому требуется добавить лицензию, также известной как имя участника-пользователя (UPN).</span><span class="sxs-lookup"><span data-stu-id="abfa1-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="abfa1-111">И, наконец укажите имя входа пользователя и имя плана лицензии и выполните следующие команды.</span><span class="sxs-lookup"><span data-stu-id="abfa1-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="abfa1-112">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="abfa1-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="abfa1-113">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="abfa1-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="abfa1-p102">Выполните команду **Get-MsolAccountSku** , чтобы просмотреть доступные планы лицензирования и число доступных лицензий в каждом плане в вашей организации. Число доступных лицензий в каждом плане — **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="abfa1-p102">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="abfa1-117">Чтобы найти нелицензированных учетные записи в вашей организации, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="abfa1-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="abfa1-p103">Учетные записи пользователей, которые имеют свойство **UsageLocation** , равное допустимый код страны альфа-2 3166-1 ISO можно назначить только лицензий. Например, "мне НРАВИТСЯ" для США и FR для Франции. Некоторые службы Office 365 не доступны в некоторых странах. Для получения дополнительных сведений см [об ограничениях лицензии](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="abfa1-p103">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="abfa1-122">Чтобы найти учетные записи, которые не имеют значений **UsageLocation** , выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="abfa1-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="abfa1-123">Чтобы задать значение **UsageLocation** учетную запись, выполните эту команду.</span><span class="sxs-lookup"><span data-stu-id="abfa1-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="abfa1-124">Пример:</span><span class="sxs-lookup"><span data-stu-id="abfa1-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="abfa1-125">Если использовать командлет **Get-MsolUser** без параметра **-All**, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="abfa1-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="abfa1-126">Назначение лицензий для учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="abfa1-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="abfa1-127">Чтобы назначить лицензии пользователя, используйте следующую команду в Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abfa1-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="abfa1-128">В этом примере показывается назначение лицензии из **litwareinc: enterprisepack** (Office 365 для предприятий E3) лицензирования плана по нелицензированных пользователей **belindan@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="abfa1-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="abfa1-129">Чтобы назначить лицензию число нелицензированных пользователей, запустите следующую команду.</span><span class="sxs-lookup"><span data-stu-id="abfa1-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="abfa1-p104">Несколько лицензий не может назначить пользователю из того же плана лицензирования. Если у вас нет достаточного количества доступных лицензий, назначаются лицензии для пользователей в том порядке, в случае возвращаемых командлетом **Get-MsolUser** , пока не истечет доступных лицензий.</span><span class="sxs-lookup"><span data-stu-id="abfa1-p104">You can't assign multiple licenses to a user from the same licensing plan. If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="abfa1-132">В этом примере назначаются лицензии из плана лицензирования **litwareinc: enterprisepack** (Office 365 для предприятий E3) всех нелицензированных пользователей:</span><span class="sxs-lookup"><span data-stu-id="abfa1-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="abfa1-133">В этом примере назначает эти же лицензии нелицензированных пользователей в отделе продаж в США:</span><span class="sxs-lookup"><span data-stu-id="abfa1-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="abfa1-134">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="abfa1-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="abfa1-135">См. также</span><span class="sxs-lookup"><span data-stu-id="abfa1-135">See also</span></span>

[<span data-ttu-id="abfa1-136">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="abfa1-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="abfa1-137">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="abfa1-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="abfa1-138">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="abfa1-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
