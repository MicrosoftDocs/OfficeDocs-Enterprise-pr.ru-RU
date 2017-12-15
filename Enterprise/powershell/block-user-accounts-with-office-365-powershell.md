---
title: "Блокировка учетных записей пользователей с помощью PowerShell в Office 365"
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
- Ent_Office_Other
- DecEntMigration
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Описание способов блокировать и разблокировать доступ к учетным записям Office 365 с помощью Office 365 PowerShell."
ms.openlocfilehash: f22656426e7aa3adf764a3f90adea84cf57a5e89
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Блокировка учетных записей пользователей с помощью PowerShell в Office 365

**Сводка:**  Описание способов блокировать и разблокировать доступ к учетным записям Office 365 с помощью Office 365 PowerShell.
  
Блокирование доступа к учетной записи Office 365 не позволяет другим пользователям с помощью учетной записи для входа и доступ к службам и данных в организации Office 365. При блокировании доступа к учетной записи, пользователь получает сообщение об ошибке при попытке входа в:
  
![Заблокированная учетная запись Office 365.](images/o365_powershell_account_blocked.png)
  
Office 365 PowerShell можно использовать для блокировки доступа к отдельным и несколько учетных записей пользователей.
  
## <a name="before-you-begin"></a>Приступая к работе

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- При блокировании учетной записи пользователя, может потребоваться в течение 24 часов вступили в силу на устройствах пользователей и клиентов.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Блокировка доступа к отдельным учетным записям пользователей с помощью PowerShell в Office 365

Используйте следующий синтаксис, чтобы заблокировать доступ к отдельной учетной записи пользователя:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Чтобы разблокировать учетную запись пользователя, выполните следующую команду:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

В любое время можно проверить заблокированных состояние учетной записи пользователя, с помощью следующей команды:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>Заблокируйте доступ к нескольким учетным записям пользователей с помощью Office 365 PowerShell

Во-первых создайте текстовый файл, содержащий одну учетную запись в каждой строке следующим образом:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
В следующие команды в текстовом файле пример — C:\My Documents\Accounts.txt. Замените путь и имя текстового файла.
    
Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $true
  ```
Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $false
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>Блокировка доступа к учетным записям пользователей с помощью модуля Azure Active Directory PowerShell 2

Чтобы использовать командлет **New-AzureADUser** из модуля Azure Active Directory PowerShell 2, сначала необходимо подключиться к подписке. Инструкции см. в разделе[Подключение с помощью модуля Azure Active Directory PowerShell 2](https://go.microsoft.com/fwlink/?linkid=842218).
  
После этого используйте следующий синтаксис, чтобы заблокировать отдельную учетную запись пользователя:
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> Параметр -ObjectID в командлете Set-AzureAD принимает либо имя учетной записи (имя участника-пользователя), либо идентификатор объекта учетной записи. 
  
В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Чтобы разблокировать эту учетную запись пользователя, выполните следующую команду:
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Для отображения имени участника-пользователя на основании отображаемое имя пользователя учетной записи пользователя, используйте следующие команды:
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

В этом примере отображается учетной записи пользователя имени участника-пользователя для пользователя с именем Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Чтобы заблокировать учетную запись на основе имени пользователя, используйте следующие команды:
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

В любое время можно проверить заблокированных состояние учетной записи пользователя, с помощью следующей команды:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

Чтобы заблокировать доступ к нескольким учетным записям пользователей, создайте текстовый файл, содержащий одно имя учетной записи в каждой строке следующим образом:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

В следующие команды в текстовом файле пример — C:\My Documents\Accounts.txt. Замените путь и имя текстового файла.
    
Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $true
```

Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $false
```

## <a name="see-also"></a>См. также
<a name="SeeAlso"> </a>

Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:
  
- [Создание учетных записей пользователей с помощью PowerShell в Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [SET-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [Новый AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

