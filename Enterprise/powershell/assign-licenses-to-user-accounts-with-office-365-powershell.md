---
title: Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123296"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365

**Сводка:**  В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.
  
Лицензирование учетных записей пользователей в Office 365 важна, так как пользователи не могут использовать какие-либо службы Office 365, пока не лицензированных своей учетной записи. Office 365 PowerShell можно использовать для эффективного назначения лицензий нелицензированных учетным записям, особенно нескольких учетных записей. 

## <a name="before-you-begin"></a>Перед началом работы
<a name="RTT"> </a>

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Командлет **Get-MsolAccountSku** используется для просмотра доступных планы лицензирования и число доступных лицензий в каждом плане в вашей организации. Число доступных лицензий в каждом плане — **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Чтобы найти нелицензированных учетные записи в вашей организации, выполните команду`Get-MsolUser -All -UnlicensedUsersOnly`
    
- Лицензии можно назначить только учетные записи пользователей, которые имеют свойство **UsageLocation** , равное допустимый код страны альфа-2 3166-1 ISO. Например, "мне НРАВИТСЯ" для США и FR для Франции. Некоторые службы Office 365 не доступны в некоторых странах. Для получения дополнительных сведений см [об ограничениях лицензии](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Чтобы найти учетные записи, которые не имеют значений **UsageLocation** , выполните команду `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Чтобы задать значение **UsageLocation** учетную запись, используйте следующий синтаксис `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Например `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- При использовании командлета **Get-MsolUser** без использования `-All` для параметра возвращаются только первые 500 учетных записей.

## <a name="assigning-licenses-to-user-accounts"></a>Назначение лицензий для учетных записей пользователей
    
Чтобы назначить лицензии пользователя, используйте следующий синтаксис в Office 365 PowerShell:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

В этом примере показывается назначение лицензии из `litwareinc:ENTERPRISEPACK` план лицензирования (Office 365 для предприятий E3) нелицензированных пользователю `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Чтобы назначить лицензию большому количеству пользователей, используйте в следующий синтаксис:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Примечания**
  
- Невозможно назначить пользователю несколько лицензий из одного плана лицензирования.
    
- Если у вас нет достаточного количества доступных лицензий, они назначаются пользователям в порядке, в котором их возвращает командлет **Get-MsolUser**, пока не закончатся.
    
В этом примере показывается назначение лицензии из `litwareinc:ENTERPRISEPACK` план лицензирования (Office 365 для предприятий E3) для всех пользователей без лицензий.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

В этом примере назначаются те же лицензии пользователям без лицензий из отдела продаж в США.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>См. также
<a name="SeeAlso"> </a>

Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:
  
- [Создание учетных записей пользователей](create-user-accounts-with-office-365-powershell.md)
    
- [Удаление и восстановление учетных записей пользователей](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Блокировки учетных записей пользователей](block-user-accounts-with-office-365-powershell.md)
    
- [Удалить лицензии у учетных записей пользователей](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [SET-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [SELECT-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

