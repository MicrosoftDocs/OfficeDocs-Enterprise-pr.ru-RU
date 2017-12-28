---
title: "Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Узнайте, как удалять и восстанавливать учетные записи пользователей Office 365, используя PowerShell."
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365

**Сводка.** Узнайте, как удалять и восстанавливать учетные записи пользователей Office 365, используя PowerShell.
  
Учетную запись пользователя, удаленную с помощью PowerShell в Office 365, можно восстановить в течение 30 дней.
  
## <a name="before-you-begin"></a>Перед началом работы

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Блокировка доступа к отдельным учетным записям пользователей с помощью PowerShell в Office 365
<a name="ShortVersion"> </a>

Чтобы удалить учетную запись пользователя, используйте следующий синтаксис:
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

В этом примере удаляется учетная запись пользователя BelindaN@litwareinc.com.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Чтобы восстановить удаленную учетную запись пользователя в течение 30 дней, используйте следующий синтаксис:
  
```
Restore-MsolUser -UserPrincipalName <Account>
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

- Если исходное имя участника-пользователя используется другой учетной записью, замените  _NewUserPrincipalName_ параметром _UserPrincipalName_, чтобы указать другое имя участника-пользователя при восстановлении учетной записи.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Удаление учетной записи пользователя с помощью модуля Azure Active Directory PowerShell 2
<a name="ShortVersion"> </a>

Чтобы использовать командлет **Remove-AzureADUser** из модуля Azure Active Directory 2 для PowerShell, сначала необходимо подключиться к подписке ([инструкции](https://go.microsoft.com/fwlink/?linkid=842218)).
  
После подключения используйте следующий синтаксис, чтобы удалить учетную запись пользователя:
  
```
Remove-AzureADUser -ObjectID <Account>
```

В этом примере удаляется учетная запись пользователя fabricec@litwareinc.com.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Параметр **-ObjectID** в командлете **Remove-AzureAD** принимает либо имя учетной записи (имя участника-пользователя), либо идентификатор объекта учетной записи.
  
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

Чтобы удалить учетную запись на основе имени пользователя, используйте следующие команды:
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>См. также
<a name="SeeAlso"> </a>

Сведения об управлении пользователями с помощью PowerShell для Office 365 см. в следующих статьях:
  
- [Создание учетных записей пользователей с помощью PowerShell в Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Блокировка учетных записей пользователей с помощью PowerShell в Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

