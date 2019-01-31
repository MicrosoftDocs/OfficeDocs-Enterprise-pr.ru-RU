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
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365

**Сводка:**  В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.
  
Пользователи не могут использовать какие-либо службы Office 365, пока не своей учетной записи будет назначена лицензия из плана лицензирования. Office 365 PowerShell позволяет быстро назначение лицензий нелицензированных учетным записям. 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Рассмотрим процедуру список планов лицензии для клиента с помощью этой команды.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Затем получите учетное имя учетной записи, к которому требуется добавить лицензию, также известной как имя участника-пользователя (UPN).

И, наконец укажите имя входа пользователя и имя плана лицензии и выполните следующие команды.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Выполните команду **Get-MsolAccountSku** , чтобы просмотреть доступные планы лицензирования и число доступных лицензий в каждом плане в вашей организации. Число доступных лицензий в каждом плане — **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Чтобы найти нелицензированных учетные записи в вашей организации, выполните следующую команду.

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
Учетные записи пользователей, которые имеют свойство **UsageLocation** , равное допустимый код страны альфа-2 3166-1 ISO можно назначить только лицензий. Например, "мне НРАВИТСЯ" для США и FR для Франции. Некоторые службы Office 365 не доступны в некоторых странах. Для получения дополнительных сведений см [об ограничениях лицензии](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Чтобы найти учетные записи, которые не имеют значений **UsageLocation** , выполните следующую команду.

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Чтобы задать значение **UsageLocation** учетную запись, выполните эту команду.

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Пример:

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Если использовать командлет **Get-MsolUser** без параметра **-All**, возвращаются только первые 500 учетных записей.

### <a name="assigning-licenses-to-user-accounts"></a>Назначение лицензий для учетных записей пользователей
    
Чтобы назначить лицензии пользователя, используйте следующую команду в Office 365 PowerShell.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

В этом примере показывается назначение лицензии из **litwareinc: enterprisepack** (Office 365 для предприятий E3) лицензирования плана по нелицензированных пользователей **belindan@litwareinc.com**:
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Чтобы назначить лицензию число нелицензированных пользователей, запустите следующую команду.
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>Несколько лицензий не может назначить пользователю из того же плана лицензирования. Если у вас нет достаточного количества доступных лицензий, назначаются лицензии для пользователей в том порядке, в случае возвращаемых командлетом **Get-MsolUser** , пока не истечет доступных лицензий.
>

В этом примере назначаются лицензии из плана лицензирования **litwareinc: enterprisepack** (Office 365 для предприятий E3) всех нелицензированных пользователей:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

В этом примере назначает эти же лицензии нелицензированных пользователей в отделе продаж в США:
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>См. также

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
