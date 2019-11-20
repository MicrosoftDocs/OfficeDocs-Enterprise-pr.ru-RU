---
title: Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: В этой статье рассказывается, как использовать PowerShell в Office 365 для просмотра учетных записей пользователей с лицензиями и пользователей без лицензий.
ms.openlocfilehash: 3869be5a0f7527f516248e7e1ef0333707f49305
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748417"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell

Учетным записям пользователей в вашей организации Office 365: могут быть назначены все лицензии или часть лицензий (или вообще ни одной доступной лицензии) из планов лицензирования, имеющихся в организации. С помощью PowerShell в Office 365 вы можете быстро найти пользователей в организации, у которых есть лицензии, и пользователей, у которых их нет.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Чтобы просмотреть список всех учетных записей пользователей в Организации, которым не назначены планы лицензирования (нелицензированные пользователи), выполните следующую команду:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Чтобы просмотреть список всех учетных записей пользователей в Организации, которым были назначены планы лицензирования (лицензированные пользователи), выполните следующую команду:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```
>[!Note]
>Чтобы получить список всех пользователей в подписке, используйте `Get-AzureAdUser -All $true` команду.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Чтобы отобразить список всех учетных записей пользователей в организации и сведения об их состояниях лицензирования, в PowerShell в Office 365 выполните указанную ниже команду.
  
```powershell
Get-MsolUser -All
```

Чтобы отобразить список всех учетных записей пользователей без лицензий в вашей организации, выполните указанную ниже команду.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Чтобы отобразить список всех учетных записей пользователей с лицензиями в вашей организации, выполните указанную ниже команду.
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>См. также

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
