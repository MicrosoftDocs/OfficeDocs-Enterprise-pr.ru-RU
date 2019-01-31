---
title: Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям.
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651223"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей

**Сводка:** Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Рассмотрим процедуру список планов лицензии для клиента с помощью этой команды.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Затем получите учетное имя учетной записи, для которого вы хотите удалить лицензии, также известной как имя участника-пользователя (UPN).

И, наконец укажите имена пользователей вход и лицензии план, удалите символы «<» и «>» и выполните следующие команды.

```
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

   
Чтобы просмотреть сведения о лицензировании плана (**AccountSkuID** ) в организации, в следующих разделах:
    
  - [Просмотр лицензий и служб с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md)
    
Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.
    
### <a name="removing-licenses-from-user-accounts"></a>Удаление лицензий из учетных записей пользователей

Чтобы удалить лицензии из учетной записи пользователя, используйте следующий синтаксис:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) с BelindaN@litwareinc.com учетной записи пользователя.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Чтобы удалить лицензии из группы лицензированных пользователей, используйте один из следующих способов:
  
- **Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) от всех accounts для сотрудников отдела продаж в США.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Использование списка определенных учетных записей** Для этого выполните следующие действия:
    
1. Создайте и сохраните текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Используйте следующий синтаксис:
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) из учетных записей пользователей, определенных в текстовый файл C:\My Documents\Accounts.txt.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Чтобы удалить лицензии из всех учетных записей пользователей, используйте следующий синтаксис:
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензий (Office 365 для предприятий E3) для всех существующих учетных записей пользователей с корпоративным лицензированием.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

Другой способ освободить лицензия — путем удаления учетной записи пользователя. Для получения дополнительных сведений см [удаления и восстановления учетных записей пользователей с Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>См. также

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

