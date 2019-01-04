---
title: Удаление учетных записей пользователей с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Узнайте, как удалять учетные записи пользователей Office 365, используя PowerShell.
ms.openlocfilehash: 0b882f3bdf9070c83baffaca65a7c80c98cd4ed9
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546470"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a>Удаление учетных записей пользователей с помощью PowerShell в Office 365

**Сводка.** Узнайте, как удалять учетные записи пользователей Office 365, используя PowerShell.
  
Чтобы удалить учетную запись пользователя, можно использовать PowerShell в Office 365.

   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

После подключения используйте следующий синтаксис, чтобы удалить учетную запись пользователя:
  
```
Remove-AzureADUser -ObjectID <sign-in name>
```

В этом примере удаляется учетная запись пользователя fabricec@litwareinc.com.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Параметр **-ObjectID** в командлете **Remove-AzureAD** принимает либо имя учетной записи, используемое для входа (имя участника-пользователя), либо идентификатор объекта учетной записи.
  
Чтобы отобразить имя учетной записи на основе имени пользователя, используйте следующие команды:
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

В этом примере отображается имя учетной записи пользователя Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Чтобы удалить учетную запись на основе отображаемого имени пользователя, используйте указанные ниже команды:
  
```
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Учетную запись пользователя, удаленную с помощью модуля Microsoft Azure Active Directory для Windows PowerShell, можно восстановить в течение 30 дней.

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


Чтобы удалить учетную запись пользователя, используйте следующий синтаксис:
  
```
Remove-MsolUser -UserPrincipalName <sign-in name>
```

В этом примере удаляется учетная запись пользователя BelindaN@litwareinc.com.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Чтобы восстановить удаленную учетную запись пользователя в течение 30 дней, используйте следующий синтаксис:
  
```
Restore-MsolUser -UserPrincipalName <sign-in name>
```

В этом примере восстанавливается удаленная учетная запись BelindaN@litwareinc.com.
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Примечания.**
  
- Чтобы просмотреть список удаленных пользователей, которых можно восстановить, выполните следующую команду:
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Если исходное имя участника-пользователя используется другой учетной записью, замените _NewUserPrincipalName_ параметром _UserPrincipalName_, чтобы указать другое имя участника-пользователя при восстановлении учетной записи.


## <a name="see-also"></a>См. также

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

