---
title: Удаление лицензий Microsoft 365 из учетных записей пользователей с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: В этой статье объясняется, как использовать PowerShell для удаления лицензий Microsoft 365, которые ранее были назначены пользователям.
ms.openlocfilehash: 5f46cfeb075d83504e3562e60e3dfd70a53dd136
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230395"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a><span data-ttu-id="e004c-103">Удаление лицензий Microsoft 365 из учетных записей пользователей с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="e004c-103">Remove Microsoft 365 licenses from user accounts with PowerShell</span></span>

<span data-ttu-id="e004c-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="e004c-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e004c-105">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="e004c-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e004c-106">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e004c-106">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="e004c-107">Затем перечислите план лицензирования для клиента с помощью этой команды.</span><span class="sxs-lookup"><span data-stu-id="e004c-107">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="e004c-108">Затем получите имя для входа учетной записи, для которой требуется удалить лицензию, также называемую именем участника-пользователя (UPN).</span><span class="sxs-lookup"><span data-stu-id="e004c-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="e004c-109">Наконец, укажите имена пользователей для входа и планов лицензирования, удалите символы "<" и ">", а затем выполните приведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="e004c-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

<span data-ttu-id="e004c-110">Чтобы удалить все лицензии для конкретной учетной записи пользователя, укажите имя пользователя для входа, удалите символы "<" и ">", а затем выполните приведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="e004c-110">To remove all of the licenses for a specific user account, specify the user sign-in name, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
if($userList -is [array]) {
for ($i=0; $i -lt $userList.Count; $i++) {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList[$i].SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList[$i].SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}
} else {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList.SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList.SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e004c-111">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e004c-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e004c-112">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e004c-112">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="e004c-113">Сведения о том, как просмотреть информацию о плане лицензирования (**AccountSkuID**) в организации, см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="e004c-113">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="e004c-114">Просмотр лицензий и служб с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="e004c-114">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="e004c-115">Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="e004c-115">View account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="e004c-116">Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="e004c-116">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="e004c-117">Удаление лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="e004c-117">Removing licenses from user accounts</span></span>

<span data-ttu-id="e004c-118">Чтобы удалить лицензии из учетной записи пользователя, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="e004c-118">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="e004c-119">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="e004c-119">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e004c-120">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e004c-120">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="e004c-121">В этом примере удаляется лицензия **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) из учетной записи пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e004c-121">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="e004c-122">Вы не можете использовать этот `Set-MsolUserLicense` командлет для отмены назначения пользователям *отмененных* лицензий.</span><span class="sxs-lookup"><span data-stu-id="e004c-122">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="e004c-123">Это необходимо сделать отдельно для каждой учетной записи пользователя в центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e004c-123">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="e004c-124">Чтобы удалить все лицензии из группы существующих лицензированных пользователей, воспользуйтесь одним из указанных ниже способов.</span><span class="sxs-lookup"><span data-stu-id="e004c-124">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="e004c-125">**Фильтрация учетных записей на основе существующего атрибута учетной записи** Для этого используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="e004c-125">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="e004c-126">В этом примере удаляются все лицензии из всех учетных записей пользователей в отделе продаж в США.</span><span class="sxs-lookup"><span data-stu-id="e004c-126">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="e004c-127">**Использование списка определенных учетных записей для конкретной лицензии** Для этого выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="e004c-127">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="e004c-128">Создайте и сохраните текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="e004c-128">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="e004c-129">Используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="e004c-129">Use the following syntax:</span></span>
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
<span data-ttu-id="e004c-130">В этом примере удаляется лицензия **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) из учетных записей пользователей, определенных в текстовом файле "Documents\Accounts.txt".</span><span class="sxs-lookup"><span data-stu-id="e004c-130">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

<span data-ttu-id="e004c-131">Чтобы удалить все лицензии из всех существующих учетных записей пользователей, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="e004c-131">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="e004c-132">Еще один способ освободить лицензию — удалить учетную запись пользователя.</span><span class="sxs-lookup"><span data-stu-id="e004c-132">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="e004c-133">Дополнительные сведения см. [в статье Удаление и восстановление учетных записей пользователей с помощью PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e004c-133">For more information, see [Delete and restore user accounts with PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e004c-134">См. также</span><span class="sxs-lookup"><span data-stu-id="e004c-134">See also</span></span>

[<span data-ttu-id="e004c-135">Управление учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="e004c-135">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e004c-136">Управление Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="e004c-136">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e004c-137">Начало работы с PowerShell для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e004c-137">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

