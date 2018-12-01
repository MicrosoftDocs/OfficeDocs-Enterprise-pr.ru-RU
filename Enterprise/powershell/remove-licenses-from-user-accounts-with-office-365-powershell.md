---
title: Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
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
ms.openlocfilehash: a993737f4bd1186a7fb5beb7fa0f6a2ae6782618
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123306"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей

**Сводка:** Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям.
  
## <a name="before-you-begin"></a>Перед началом работы

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Чтобы просмотреть сведения о лицензировании плана (**AccountSkuID** ) в организации, в следующих разделах:
    
  - [Просмотр лицензий и служб с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md)
    
- Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.
    
## <a name="removing-licenses-from-user-accounts"></a>Удаление лицензий из учетных записей пользователей

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

Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:
  
- [Создание учетных записей пользователей с помощью PowerShell в Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Блокировка учетных записей пользователей с помощью PowerShell в Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [SET-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

