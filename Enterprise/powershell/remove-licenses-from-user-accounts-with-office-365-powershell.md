---
title: Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/26/2020
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
description: В этой статье объясняется, как использовать PowerShell для Office 365 для удаления лицензий Office 365, которые ранее были назначены пользователям.
ms.openlocfilehash: f5b1dc18dfd53548d1e49a3193315acc0343f816
ms.sourcegitcommit: 0c2d4cfb4d1b21ea93bcc6eb52421548db34b1e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2020
ms.locfileid: "44374458"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Затем перечислите план лицензирования для клиента с помощью этой команды.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Затем получите имя для входа учетной записи, для которой требуется удалить лицензию, также называемую именем участника-пользователя (UPN).

Наконец, укажите имена пользователей для входа и планов лицензирования, удалите символы "<" и ">", а затем выполните приведенные ниже команды.

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

Чтобы удалить все лицензии для конкретной учетной записи пользователя, укажите имя пользователя для входа, удалите символы "<" и ">", а затем выполните приведенные ниже команды.

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Сведения о том, как просмотреть информацию о плане лицензирования (**AccountSkuID**) в организации, см. в следующих статьях:
    
  - [Просмотр лицензий и служб с помощью PowerShell в Office 365](view-licenses-and-services-with-office-365-powershell.md) .
    
  - [Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md) .
    
Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.
    
### <a name="removing-licenses-from-user-accounts"></a>Удаление лицензий из учетных записей пользователей

Чтобы удалить лицензии из учетной записи пользователя, используйте следующий синтаксис:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени. Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>

В этом примере удаляется лицензия **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) из учетной записи пользователя BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Вы не можете использовать этот `Set-MsolUserLicense` командлет для отмены назначения пользователям *отмененных* лицензий. Это необходимо сделать отдельно для каждой учетной записи пользователя в центре администрирования Microsoft 365.
>

Чтобы удалить все лицензии из группы существующих лицензированных пользователей, воспользуйтесь одним из указанных ниже способов.
  
- **Фильтрация учетных записей на основе существующего атрибута учетной записи** Для этого используйте следующий синтаксис:
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

В этом примере удаляются все лицензии из всех учетных записей пользователей в отделе продаж в США.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Использование списка определенных учетных записей для конкретной лицензии** Для этого выполните указанные ниже действия.
    
1. Создайте и сохраните текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Используйте следующий синтаксис:
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
В этом примере удаляется лицензия **litwareinc: ENTERPRISEPACK** (Office 365 корпоративный E3) из учетных записей пользователей, определенных в текстовом файле "е Documents\Accounts.txt.".
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

Чтобы удалить все лицензии из всех существующих учетных записей пользователей, используйте следующий синтаксис:
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Еще один способ освободить лицензию — удалить учетную запись пользователя. Дополнительные сведения см. [в статье Удаление и восстановление учетных записей пользователей с помощью Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>См. также

[Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

