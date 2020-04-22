---
title: Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/20/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: В этой статье объясняется, как использовать PowerShell для Office 365 для удаления лицензий Office 365, которые ранее были назначены пользователям.
ms.openlocfilehash: ea762e992056ac3265336055eabb860f67482093
ms.sourcegitcommit: f2e640ffdbef95c6d98845f85fd9bea21a7388aa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "43580926"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="2d658-103">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="2d658-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="2d658-104">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="2d658-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="2d658-105">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="2d658-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="2d658-106">Затем перечислите план лицензирования для клиента с помощью этой команды.</span><span class="sxs-lookup"><span data-stu-id="2d658-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="2d658-107">Затем получите имя для входа учетной записи, для которой требуется удалить лицензию, также называемую именем участника-пользователя (UPN).</span><span class="sxs-lookup"><span data-stu-id="2d658-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="2d658-108">Наконец, укажите имена пользователей для входа и планов лицензирования, удалите символы "<" и ">", а затем выполните приведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="2d658-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="2d658-109">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d658-109">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="2d658-110">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2d658-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="2d658-111">Сведения о плане лицензирования (**AccountSkuID** ) в Организации можно просмотреть в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="2d658-111">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - <span data-ttu-id="2d658-112">[Просмотр лицензий и служб с помощью PowerShell в Office 365](view-licenses-and-services-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="2d658-112">[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)</span></span>
    
  - <span data-ttu-id="2d658-113">[Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="2d658-113">[View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)</span></span>
    
<span data-ttu-id="2d658-114">Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="2d658-114">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="2d658-115">Удаление лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="2d658-115">Removing licenses from user accounts</span></span>

<span data-ttu-id="2d658-116">Чтобы удалить лицензии из учетной записи пользователя, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2d658-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="2d658-117">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="2d658-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="2d658-118">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d658-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="2d658-119">В этом примере удаляется лицензия **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) из учетной записи пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="2d658-119">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="2d658-120">Вы не можете использовать `Set-MsolUserLicense` этот командлет для отмены назначения пользователям *отмененных* лицензий.</span><span class="sxs-lookup"><span data-stu-id="2d658-120">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="2d658-121">Это необходимо сделать отдельно для каждой учетной записи пользователя в центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2d658-121">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="2d658-122">Чтобы удалить лицензии из группы лицензированных пользователей, используйте один из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="2d658-122">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="2d658-123">**Фильтрация учетных записей на основе существующего атрибута учетной записи** Для этого используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2d658-123">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="2d658-124">В этом примере удаляются лицензии **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) из всех учетных записей для пользователей в отделе продаж в США.</span><span class="sxs-lookup"><span data-stu-id="2d658-124">This example removes the  **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="2d658-125">**Использование списка определенных учетных записей** Для этого выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="2d658-125">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="2d658-126">Создайте и сохраните текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="2d658-126">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="2d658-127">Используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2d658-127">Use the following syntax:</span></span>
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

<span data-ttu-id="2d658-128">В этом примере удаляется лицензия **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) из учетных записей пользователей, определенных в текстовом файле "е Documents\Accounts.txt.".</span><span class="sxs-lookup"><span data-stu-id="2d658-128">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="2d658-129">Чтобы удалить все лицензии из всех существующих учетных записей пользователей, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2d658-129">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$users = Get-MsolUser -All | where {$_.isLicensed -eq $true}
ForEach($user in $users)
{
$licenses = $user.Licenses.AccountSkuId
ForEach ($lic in $licenses)
{ Set-MsolUserLicense -UserPrincipalName $user.UserPrincipalName -RemoveLicenses $lic }
}
```

<span data-ttu-id="2d658-130">Еще один способ освободить лицензию — удалить учетную запись пользователя.</span><span class="sxs-lookup"><span data-stu-id="2d658-130">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="2d658-131">Дополнительные сведения см. [в статье Удаление и восстановление учетных записей пользователей с помощью Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="2d658-131">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2d658-132">См. также</span><span class="sxs-lookup"><span data-stu-id="2d658-132">See also</span></span>

[<span data-ttu-id="2d658-133">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d658-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="2d658-134">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="2d658-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2d658-135">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d658-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

