---
title: Блокировка учетных записей пользователей с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Сведения об использовании PowerShell в Office 365 для блокировки и разблокировки доступа к учетным записям Office 365.
ms.openlocfilehash: 2ebed63de7cddd536b42000028cabd3c71cec31b
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072251"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Блокировка учетных записей пользователей с помощью PowerShell в Office 365

Блокировка доступа к учетной записи Office 365 позволяет всем пользователям использовать эту учетную запись для входа и доступа к службам и данным в организации Office 365. Вы можете использовать Office 365 PowerShell, чтобы заблокировать доступ к отдельным и нескольким учетным записям пользователей.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Блокировка доступа к отдельным учетным записям пользователей

Используйте следующий синтаксис, чтобы заблокировать отдельную учетную запись пользователя:
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Параметр – ObjectID в командлете Set – AzureAD принимает либо имя входа учетной записи, также называемое именем участника пользователя, либо идентификатор объекта учетной записи. 
  
В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Чтобы разблокировать эту учетную запись пользователя, выполните следующую команду:
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Чтобы отобразить учетную запись участника-пользователя на основе отображаемого имени пользователя, используйте следующие команды:
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

В этом примере отображается имя участника-пользователя для учетной записи пользователя с именем Caleb Sills.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Чтобы заблокировать учетную запись на основе отображаемого имени пользователя, используйте следующие команды:
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

В любое время вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Блокировка доступа к нескольким учетным записям пользователей

Чтобы заблокировать доступ к нескольким учетным записям пользователей, создайте текстовый файл с одним именем входа учетной записи в каждой строке, как показано ниже.
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

В приведенных ниже командах приведен пример текстового файла "\ мои Documents\Accounts.txt.". Замените путь и имя файла для текстового файла.
  
Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
### <a name="block-access-to-individual-user-accounts"></a>Блокировка доступа к отдельным учетным записям пользователей

Используйте следующий синтаксис, чтобы заблокировать доступ к отдельной учетной записи пользователя:
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени. Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>

В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Чтобы разблокировать учетную запись пользователя, выполните следующую команду:
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

В любое время вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Блокировка доступа к нескольким учетным записям пользователей

Сначала создайте текстовый файл, который содержит одну учетную запись в каждой строке, как показано ниже.
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

В приведенных ниже командах приведен пример текстового файла "\ мои Documents\Accounts.txt.". Замените путь и имя файла для текстового файла.
    
Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>См. также

[Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
