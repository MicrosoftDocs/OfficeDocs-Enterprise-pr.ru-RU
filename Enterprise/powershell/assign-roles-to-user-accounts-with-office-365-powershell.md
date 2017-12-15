---
title: "Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365"
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "Сводка. Используйте PowerShell в Office 365 и командлет Add-MsolRoleMember для назначения ролей учетным записям пользователей."
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365

 **Сводка:** Используйте командлет **Add-MsolRoleMember** и Office 365 PowerShell для назначения ролей для учетных записей пользователей.
  
Можно быстро и легко назначить роли для учетных записей пользователей с помощью Office 365 PowerShell, указав отображаемое имя учетной записи пользователя и имя роли.
  
## <a name="before-you-begin"></a>Приступая к работе

Чтобы выполнять процедуры, описанные в этой статье, необходимо подключиться к PowerShell в Office 365, используя учетную запись глобального администратора. Инструкции см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="for-a-single-role-change"></a>Изменение одной роли

Определите следующее:
  
- Учетная запись пользователя, которую вы хотите настроить.
    
    Чтобы указать учетную запись пользователя, необходимо определить его отображаемого имени. Чтобы получить полный список учетных записей, используйте следующую команду:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Эта команда выводит учетные записи пользователей, отсортированное по отображаемому имени, по одному экрану за раз. Вы можете отфильтровать список, используя командлет **Where**. Вот пример:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Эта команда выводит только учетные записи пользователей, отображаемое имя которых начинается со слова "John".
    
- Роль, которую вы хотите назначить.
    
    Чтобы отобразить список доступных ролей, используйте эту команду:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

После того как вы определили отображаемое имя учетной записи и имя роли, используйте эти команды, чтобы назначить роль учетной записи:
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Скопируйте команды и вставьте их в "Блокнот". Переменные **$dispName** и **$roleName** замените текст описания их значения, удалите \< и > символов и оставьте кавычки. Скопируйте изменений в строках и вставьте их в вашем окне Windows Azure модуль Active Directory для Windows PowerShell для их запуска. Кроме того можно использовать Windows PowerShell интегрированная скрипт среды (ISE).
  
Вот пример полного набора команд:
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>Изменение нескольких ролей

Определите следующее:
  
- Какие учетные записи пользователей вы хотите настроить.
    
    Чтобы указать учетную запись пользователя, необходимо определить ее отображаемое имя. Чтобы получить список учетных записей, используйте эту команду:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Эта команда выводит список отображаемое имя все учетные записи пользователей, отсортированные по отображаемому имени, на один экран. С помощью командлета **которых** можно отфильтровать список с небольшим набором. Ниже приведен пример:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Эта команда выводит только учетные записи пользователей, отображаемое имя которых начинается со слова "John".
    
- Какие роли вы хотите назначить каждой учетной записи пользователя.
    
    Чтобы отобразить список доступных ролей, используйте эту команду:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

После этого создайте текстовый CSV-файл, содержащий поля DisplayName и RoleName. Вот пример:
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

Затем укажите расположение CSV-файла и запустите получившиеся команды в командной строке PowerShell.
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>See also

#### 

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
#### 

[Add-MsolRoleMember](https://msdn.microsoft.com/library/dn194120.aspx)

