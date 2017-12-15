---
title: "Просмотр учетных записей пользователей с помощью PowerShell для Office 365"
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "Обзор: Просмотр, список или отображение учетные записи пользователей с Office 365 PowerShell разными способами."
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Просмотр учетных записей пользователей с помощью PowerShell для Office 365

 **Сводка:** Просмотр, список или отображение учетные записи пользователей с Office 365 PowerShell разными способами.
  
Несмотря на то, что центр администрирования Office 365 можно использовать для просмотра учетных записей для клиента Office 365, можно с помощью Office 365 PowerShell и выполнить некоторые действия, которые невозможно Центр администрирования Office 365.
  
## <a name="before-you-begin"></a>Приступая к работе

Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="display-office-365-user-account-information"></a>Отображение сведений об учетных записях пользователей Office 365

Чтобы просмотреть полный список учетных записей пользователей, выполните следующую команду в командной строки на Office 365 PowerShell или PowerShell интегрированная скрипт среды (ISE).
  
```
Get-MsolUser
```

Выходные данные должны выглядеть примерно следующим образом:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Командлет **Get-MsolUser** также имеет ряд параметров для фильтрации набора отображаются учетные записи пользователей. Например для списка нелицензированных пользователей (пользователей, которые были добавлены в Office 365, но еще не были лицензии на использование любой из служб), выполните следующую команду.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Выходные данные должны выглядеть примерно следующим образом:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Дополнительные сведения о дополнительных параметров для фильтрации на отображение набор учетных записей пользователей отображается, можно [Такую](https://msdn.microsoft.com/library/azure/dn194133.aspx) .
  
Чтобы быть более Выборочный о список учетных записей для отображения, вы можно использовать командлет **Where-Object** в сочетании с помощью командлета **Get-MsolUser** . Чтобы объединить два командлеты, мы используем символ «вертикальная черта» «|», который сообщает Office 365 PowerShell результаты одной команды и отправьте его в следующей команде. Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).
    
- Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ). В фигурных скобках, команда указывает, что Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( ** $ \_. UsageLocation** ), не является указанного ( **-eq $Null** ).
    
Выходные данные должны выглядеть примерно следующим образом:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

Свойство **UsageLocation** — только один из многих свойства, связанные с учетной записью пользователя. Чтобы просмотреть все свойства для учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (*) для отображения их все для учетной записи пользователя. Ниже приведен пример:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Например в этом списке **Город** — это имя свойства учетной записи пользователя. Это означает, что для получения списка всех учетных записей пользователей для пользователей в Лондон можно использовать следующую команду:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Синтаксис командлет **Where-Object** , показано в следующих примерах **Where-Object {$\_.** [имя свойства учетной записи пользователя] [оператор сравнения] [значение] **}**. > [оператор сравнения] — это **-eq** значение, **-ne** для не равно, **-lt** меньше, чем **-gt** для больше, чем и другие пользователи > [значение] — это строка (последовательность букв, цифр и других знаков), числовое значение или **$Null** для не определена > [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) более подробные сведения.
  
Можно проверить состояние блокировки учетной записи пользователя, с помощью следующей команды:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>Выбор отображаемых свойств учетных записей пользователей

Командлет [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) по умолчанию отображает три свойства учетных записей пользователей:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
При необходимости в дополнительных свойств, например отдела, для работы пользователя и страны или региона, где пользователь использует службы Office 365, можно запустить **Такую** в сочетании с командлет **Select-Object** , чтобы указать список учетной записи пользователя свойства. Ниже приведен пример:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).
    
- Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).
    
Выходные данные должны выглядеть примерно следующим образом:
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

Командлет **Select-Object** позволяет выбрать команду, чтобы отобразить свойства. Чтобы просмотреть все свойства для учетных записей пользователей, используйте подстановочный знак (*) для отображения их все для учетной записи пользователя. Ниже приведен пример:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Чтобы быть более Выборочный о список учетных записей для отображения, вы можно также использовать командлет **Where-Object** . Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).
    
- Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ) и отправлять полученные сведения к следующей команде ( **|** ). В фигурных скобках, команда рекомендует Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( ** $ \_. UsageLocation** ), не является указанного ( **-eq $Null** ).
    
- Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).
    
Выходные данные должны выглядеть примерно следующим образом:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>Отображение учетных записей пользователей с помощью модуля PowerShell для Azure Active Directory 2

Чтобы отобразить свойства для учетных записей пользователей с помощью модуля Azure Active Directory версии 2 PowerShell, командлет [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Но для начала необходимо подключиться к своей подписке. Инструкции в разделе[подключение с помощью модуля Azure Active Directory версии 2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="display-office-365-user-account-information"></a>Отображение сведений об учетных записях пользователей Office 365

Чтобы просмотреть полный список учетных записей пользователей, выполните следующую команду в командной строки на Office 365 PowerShell или PowerShell интегрированная скрипт среды (ISE).
  
```
Get-AzureADUser
```

Командлет **Get-AzureADUser** по умолчанию отображает три свойства учетных записей пользователей:
  
- ObjectID
    
- DisplayName
    
- UserPrincipalName
    
Чтобы быть более Выборочный о список учетных записей для отображения, вы можно использовать командлет **Where-Object** в сочетании с помощью командлета **Get-AzureADUser** . Чтобы объединить два командлеты, мы используем символ «вертикальная черта» «|», который сообщает Office 365 PowerShell результаты одной команды и отправьте его в следующей команде. Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).
    
- Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ). В фигурных скобках, команда указывает, что Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( ** $ \_. UsageLocation** ), не является указанного ( **-eq $Null** ).
    
Свойство **UsageLocation** — только один из многих свойства, связанные с учетной записью пользователя. Чтобы просмотреть все свойства для учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (*) для отображения их все для учетной записи пользователя, одну страницу за раз (или **более** ). Ниже приведен пример:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

Например **Город** — это имя свойства учетной записи пользователя. Это означает, что для получения списка всех учетных записей пользователей для пользователей в Лондон можно использовать следующую команду:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Синтаксис командлет **Where-Object** , показано в следующих примерах **Where-Object {$\_.** [имя свойства учетной записи пользователя] [оператор сравнения] [значение] **}**. > [оператор сравнения] — это **-eq** значение, **-ne** для не равно, **-lt** меньше, чем **-gt** для больше, чем и другие пользователи > [значение] — это строка (последовательность букв, цифр и других знаков), числовое значение или **$Null** для не определена >[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) более подробные сведения.
  
### <a name="select-the-user-account-properties-to-display"></a>Выбор отображаемых свойств учетных записей пользователей

Командлет **Get-AzureADUser** по умолчанию отображает ObjectID, DisplayName и UserPrincipalName свойства учетных записей пользователей. При необходимости в дополнительных свойств, например отдела, для работы пользователя и страны или региона, где пользователь использует службы Office 365, можно запустить **Get-AzureADUser** в сочетании с командлет **Select-Object** , чтобы указать список пользователей Свойства учетной записи. Ниже приведен пример:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).
    
- Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).
    
Чтобы быть более Выборочный о список учетных записей для отображения, вы можно также использовать командлет **Where-Object** . Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).
    
- Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ) и отправлять полученные сведения к следующей команде ( **|** ). В фигурных скобках, команда рекомендует Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( ** $ \_. UsageLocation** ), не является указанного ( **-eq $Null** ).
    
- Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).
    
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

||
|:-----|
|![Короткие значок обучения LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Создать в Office 365?**         Обнаружение Бесплатные курсы видео для [ИТ-специалистов и администраторов Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), с LinkedIn обучения. |
   
## <a name="see-also"></a>See also

#### 

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

