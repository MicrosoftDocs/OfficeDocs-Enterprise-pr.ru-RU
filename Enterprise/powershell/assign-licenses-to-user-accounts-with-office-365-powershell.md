---
title: Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/26/2019
audience: Admin
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
search.appverid:
- MET150
description: Инструкции по использованию Office 365 PowerShell для назначения лицензии Office 365 пользователям без лицензий.
ms.openlocfilehash: 22cc5377557464ac6d67833381b96ac01382bc4b
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707006"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="bc84f-103">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="bc84f-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="bc84f-104">**Сводка:**  Инструкции по использованию Office 365 PowerShell для назначения лицензии Office 365 пользователям без лицензий.</span><span class="sxs-lookup"><span data-stu-id="bc84f-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="bc84f-105">Пользователи не могут использовать службы Office 365, пока их учетной записи не назначена лицензия из плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="bc84f-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="bc84f-106">Вы можете быстро назначить лицензии для нелицензированных учетных записей с помощью PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc84f-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="bc84f-107">Учетным записям пользователей должно быть назначено расположение.</span><span class="sxs-lookup"><span data-stu-id="bc84f-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="bc84f-108">Это можно сделать в свойствах учетной записи пользователя в центре администрирования Microsoft 365 или PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc84f-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="bc84f-109">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="bc84f-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="bc84f-110">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="bc84f-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="bc84f-111">Затем перечислите план лицензирования для клиента с помощью этой команды.</span><span class="sxs-lookup"><span data-stu-id="bc84f-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="bc84f-112">Затем получите имя для входа учетной записи, к которой требуется добавить лицензию, также называемую именем участника-пользователя (UPN).</span><span class="sxs-lookup"><span data-stu-id="bc84f-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="bc84f-113">Затем убедитесь, что для учетной записи пользователя назначено место использования.</span><span class="sxs-lookup"><span data-stu-id="bc84f-113">Next, ensure that the user account has a usage location assigned.</span></span>

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="bc84f-114">Если местоположение использования не назначено, вы можете назначить его с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="bc84f-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="bc84f-115">Наконец, укажите имя пользователя для входа и имя плана лицензирования и выполните указанные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="bc84f-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="bc84f-116">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc84f-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="bc84f-117">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="bc84f-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="bc84f-118">Выполните команду **Get – MsolAccountSku** , чтобы просмотреть доступные планы лицензирования и число доступных лицензий в каждом плане в Организации.</span><span class="sxs-lookup"><span data-stu-id="bc84f-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="bc84f-119">Число доступных лицензий в каждом плане — **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="bc84f-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="bc84f-120">Для получения дополнительных сведений о планах лицензирования, лицензиях и службах ознакомьтесь со статьей [Просмотр лицензий и служб с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bc84f-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="bc84f-121">Чтобы найти нелицензированные учетные записи в Организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="bc84f-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="bc84f-122">Вы можете назначать лицензии только тем пользователям, у которых для свойства **UsageLocation** задан действительный код страны ISO 3166-1 Alpha-2.</span><span class="sxs-lookup"><span data-stu-id="bc84f-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="bc84f-123">Важно указать это значение, так как некоторые службы O365_W14_2nd недоступны в определенных странах.</span><span class="sxs-lookup"><span data-stu-id="bc84f-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="bc84f-124">Некоторые службы Office 365 недоступны в некоторых странах.</span><span class="sxs-lookup"><span data-stu-id="bc84f-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="bc84f-125">Более подробную информацию можно узнать в статье [ограничения лицензирования](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="bc84f-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="bc84f-126">Чтобы найти учетные записи, для которых не задано значение **UsageLocation** , выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="bc84f-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="bc84f-127">Чтобы задать значение **UsageLocation** для учетной записи, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="bc84f-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="bc84f-128">Пример:</span><span class="sxs-lookup"><span data-stu-id="bc84f-128">For example:</span></span>

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="bc84f-129">Если использовать командлет **Get-MsolUser** без параметра **-All**, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="bc84f-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="bc84f-130">Назначение лицензий учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="bc84f-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="bc84f-131">Чтобы назначить лицензию пользователю, используйте следующую команду в Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc84f-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="bc84f-132">В этом примере назначается лицензия из плана лицензирования **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) для нелицензированного пользователя **\@белиндан litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="bc84f-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="bc84f-133">Чтобы назначить лицензию большому количеству нелицензированных пользователей, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="bc84f-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="bc84f-134">Невозможно назначить пользователю несколько лицензий из одного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="bc84f-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="bc84f-135">Если у вас нет достаточного количества доступных лицензий, они назначаются пользователям в порядке, в котором их возвращает командлет **Get-MsolUser**, пока не закончатся.</span><span class="sxs-lookup"><span data-stu-id="bc84f-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="bc84f-136">В этом примере назначаются лицензии из плана лицензирования **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) для всех нелицензированных пользователей:</span><span class="sxs-lookup"><span data-stu-id="bc84f-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="bc84f-137">В этом примере для нелицензированных пользователей назначаются те же лицензии в отделе продаж в США.</span><span class="sxs-lookup"><span data-stu-id="bc84f-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="bc84f-138">Перемещение пользователя в другую подписку (план лицензирования) с помощью модуля Azure Active Directory PowerShell для Graph</span><span class="sxs-lookup"><span data-stu-id="bc84f-138">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="bc84f-139">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="bc84f-139">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="bc84f-140">Затем получите имя для входа учетной записи пользователя, для которой требуется сменить подписку, также называемую именем участника-пользователя (UPN).</span><span class="sxs-lookup"><span data-stu-id="bc84f-140">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="bc84f-141">Затем перечислите подписки (планы лицензирования) для вашего клиента с помощью этой команды.</span><span class="sxs-lookup"><span data-stu-id="bc84f-141">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="bc84f-142">Затем перечислите подписку на текущую учетную запись пользователя с помощью этих команд.</span><span class="sxs-lookup"><span data-stu-id="bc84f-142">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="bc84f-143">Определите подписку пользователя (из подписки) и подписку, на которую пользователь перемещается (в подписку).</span><span class="sxs-lookup"><span data-stu-id="bc84f-143">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="bc84f-144">Наконец, укажите имена подписок "Кому" и "от" (номера деталей SKU) и выполните приведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="bc84f-144">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="bc84f-145">Вы можете проверить изменение подписки для учетной записи пользователя с помощью этих команд.</span><span class="sxs-lookup"><span data-stu-id="bc84f-145">You can verify the change in subscription for the user account with these commands.</span></span>

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="new-to-office-365"></a><span data-ttu-id="bc84f-146">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="bc84f-146">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="bc84f-147">См. также</span><span class="sxs-lookup"><span data-stu-id="bc84f-147">See also</span></span>

[<span data-ttu-id="bc84f-148">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc84f-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="bc84f-149">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="bc84f-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="bc84f-150">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc84f-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
