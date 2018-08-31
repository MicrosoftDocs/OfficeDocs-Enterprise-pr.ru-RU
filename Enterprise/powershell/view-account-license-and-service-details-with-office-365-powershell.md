---
title: Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Объясняет, как использовать Office 365 PowerShell для определения служб Office 365, которые были назначены пользователям.
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223111"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365

**Сводка:** Объясняет, как использовать Office 365 PowerShell для определения служб Office 365, которые были назначены пользователям.
  
В Office 365, лицензируемые из планы лицензирования (также называемое номера SKU или Office 365 планы) предоставить пользователям доступ к службам Office 365, определенных для этих планов. Тем не менее пользователь может отсутствовать доступ ко всем службам, которые доступны в лицензию, назначенных им. Office 365 PowerShell можно использовать для просмотра состояния службы на учетные записи пользователей. 

## <a name="before-you-begin"></a>Перед началом работы

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Используйте команды `Get-MsolAccountSku` и `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` для поиска со следующими сведениями:
    
  - Планы лицензирования, доступные в организации.
    
  - Службы, доступные в каждом плане лицензирования, и порядок, в котором они располагаются (индекс).
    
     Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Используйте команду `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` поиск лицензий, назначенных пользователю, и порядок, в котором они являются из списка (индекс).
    
- Если использовать командлет **Get-MsolUser** без параметра _All_, возвращаются только первые 500 учетных записей.
    

## <a name="to-view-services-for-a-user-account"></a>Чтобы просмотреть службы для учетной записи пользователя

Чтобы просмотреть все, которые пользователь имеет доступ к службам Office 365, используйте следующий синтаксис:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

В этом примере показано служб, с которыми пользователь BelindaN@litwareinc.com имеет доступ. Это показывает службы, которые связаны с всех лицензий, которые были им назначены своей учетной записи.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Этот код показывает службы, к которым у пользователя BelindaN@litwareinc.com есть доступ по первой назначенной ей лицензии (индекс 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Чтобы найти всех лицензированных пользователей, для которых включены или отключены определенные службы, используйте следующий синтаксис:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

В этих примерах используются следующие сведения:
  
- Лицензии, который предоставляет доступ к службам Office 365, которые мы будем рады — это первый лицензии, назначенной для всех пользователей (номер индекса 0).
    
- Службы Office 365, которые мы будем рады, Скайп для бизнеса в Интернет и Exchange Online. Для лицензий, которые связаны с план лицензирования, Скайп для бизнеса в Интернет — 6-й служба, из списка (номер индекса — 5), и Exchange Online — 9 служба перечисленных (индекс равен 8).
    
В этом примере возвращаются все лицензированных пользователей, которым разрешена Скайп для бизнеса в Интернет и Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

В этом примере возвращаются всех лицензированных пользователей, не включенных в Скайп для бизнеса в Интернет или Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Чтобы просмотреть все службы для пользователя, которому назначена *несколько лицензий*, используйте следующий синтаксис:

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a>См. также

Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:
  
- [Создание учетных записей пользователей с помощью PowerShell в Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Блокировка учетных записей пользователей с помощью PowerShell в Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [SELECT-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]