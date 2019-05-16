---
title: Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: В этой статье объясняется, как использовать PowerShell в Office 365 для определения служб Office 365, назначенных пользователям.
ms.openlocfilehash: 608d26dfc4aa1be782f94aa3b1ba5f66a0378f1e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071125"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365

**Сводка:** В этой статье объясняется, как использовать PowerShell в Office 365 для определения служб Office 365, назначенных пользователям.
  
В Office 365 лицензии из планов лицензирования (которые также называются конфигурациями и планами Office 365) предоставляют пользователям доступ к службам Office 365, определенным для этих планов. Однако у пользователя могут отсутствовать права на доступ ко всем службам, которые доступны в лицензии, назначенной им в настоящее время. Вы можете использовать Office 365 PowerShell для просмотра состояния служб на учетных записях пользователей. 

Для получения дополнительных сведений о планах лицензирования, лицензиях и службах ознакомьтесь со статьей [Просмотр лицензий и служб с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Затем перечислите план лицензирования для клиента с помощью этой команды.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Используйте эти команды для перечисления служб, доступных в каждом плане лицензирования.

```
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
````

Используйте эти команды для перечисления лицензий, назначенных учетной записи пользователя.

````
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
````

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Затем выполните эту команду, чтобы получить список планов лицензирования, доступных в Организации. 

```
Get-MsolAccountSku
```

Затем выполните эту команду, чтобы получить список служб, доступных в каждом плане лицензирования, и порядок, в котором они указаны (номер индекса).

````
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
````
  
Используйте эту команду, чтобы получить список лицензий, назначенных пользователю, и порядок их следования (номер индекса).

````
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
````

>[!Note]
>Если использовать командлет **Get-MsolUser** без параметра _All_, возвращаются только первые 500 учетных записей.
>
   

### <a name="to-view-services-for-a-user-account"></a>Просмотр служб для учетной записи пользователя

Чтобы просмотреть все службы Office 365, к которым у пользователя есть доступ, используйте следующий синтаксис:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

В этом примере показаны службы, к которым у пользователя BelindaN@litwareinc.com есть доступ. Этот код показывает службы, связанные со всеми лицензиями, назначенными ее учетной записи.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Этот код показывает службы, к которым у пользователя BelindaN@litwareinc.com есть доступ по первой назначенной ей лицензии (индекс 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Чтобы просмотреть все службы для пользователя, которому назначено *несколько лицензий*, используйте следующий синтаксис:

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

  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>См. также

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
