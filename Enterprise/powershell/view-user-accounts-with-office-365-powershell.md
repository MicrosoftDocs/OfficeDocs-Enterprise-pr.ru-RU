---
title: Просмотр учетных записей пользователей с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Сводка: Просмотр, список или отображение учетных записей пользователей различными способами с помощью Office 365 PowerShell.'
ms.openlocfilehash: e1a99aef4f2045dcba8d7f3894ef82f9e7c36a15
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071105"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Просмотр учетных записей пользователей с помощью PowerShell для Office 365

**Сводка:** Просмотр учетных записей пользователей различными способами с помощью Office 365 PowerShell.
  
Несмотря на то, что вы можете использовать центр администрирования Office 365 для просмотра учетных записей клиента Office 365, вы также можете использовать PowerShell для Office 365 и выполнять некоторые действия, которые не могут находиться в центре администрирования Office 365.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Просмотр всех учетных записей

Чтобы отобразить полный список учетных записей пользователей, выполните следующую команду:
  
```
Get-AzureADUser
```

Выходные данные должны выглядеть примерно следующим образом:
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>Просмотр определенной учетной записи

Чтобы отобразить определенную учетную запись пользователя, введите имя учетной записи пользователя, также называемое именем участника-пользователя (UPN), удалите символы "_Лт_" и "_Гт_", а затем выполните следующую команду:
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Вот пример:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Просмотр дополнительных значений свойств для конкретной учетной записи

По умолчанию командлет **Get – AzureADUser** отображает свойства ObjectID, DisplayName и userPrincipalName для учетных записей.

Чтобы сделать более избирательным список отображаемых свойств, можно использовать командлет **Select – Object** в сочетании с командлетом **Get – AzureADUser** . Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который сообщает PowerShell Active Directory PowerShell для Graph, чтобы получить результаты одной команды и отправить ее следующей команде. Ниже приведен пример команды, которая отображает DisplayName, Department и UsageLocation для каждой учетной записи пользователя:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Эта команда дает инструкцию PowerShell для Office 365:
  
- Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).
    
- Отображение только имени, отдела и места использования учетной записи пользователя ( **Select-Object DisplayName, Department, UsageLocation** ).
  
Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (*), чтобы отображать их все для конкретной учетной записи пользователя. Вот пример:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

В качестве другого примера можно проверить включенное состояние конкретной учетной записи пользователя с помощью следующей команды:
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Просмотр некоторых учетных записей на основе общего свойства

Чтобы еще точнее отфильтровать список отображаемых учетных записей, можно использовать сочетание командлетов **Where-Object** и **Get-AzureADUser**. Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который сообщает PowerShell Active Directory PowerShell для Graph, чтобы получить результаты одной команды и отправить ее следующей команде. Ниже приведен пример команды, которая выводит только учетные записи, для которых не указано место использования:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Эта команда указывает Azure Active Directory PowerShell для Graph:
  
- Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).
    
- Найдите все учетные записи пользователей с незаданной областью использования ( **где-Object {$\_. UsageLocation-EQ $Null}** ). В фигурных скобках команда инструктирует Office 365 PowerShell, чтобы найти только те учетные записи, в которых свойство учетной записи пользователя UsageLocation ( ** $ \_. UsageLocation** ) не указан ( **-EQ $NULL** ).
    
**UsageLocation** — лишь одно из многих свойств, связанных с учетной записью пользователя. Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (*), чтобы отображать их все для конкретной учетной записи пользователя. Вот пример:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Например, **City** для этого списка — имя свойства, принадлежащего учетной записи пользователя. Это значит, что перечислить все учетные записи пользователей, проживающих в Лондоне, можно с помощью такой команды:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Для командлета **Where-Object** , показанного в этих примерах, используется синтаксис **Where-\_Object {$.** [имя свойства учетной записи пользователя] [оператор сравнения] оно **}**. _гт_ [оператор сравнения] имеет значение **-EQ** для Equals, **-Ne** для Not Equals, **-lt** для "меньше, чем", "-gt" для "больше чем", " **-gt** " и других.  [Value] как правило, это строка (последовательность букв, цифр и других знаков), числовое значение или **$null** унспеЦифиед_гт_ для получения дополнительных сведений см [](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Просмотр всех учетных записей

Чтобы отобразить полный список учетных записей пользователей, выполните следующую команду:
  
```
Get-MsolUser
```

Выходные данные должны выглядеть примерно следующим образом:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

У командлета **Get-MsolUser** также есть ряд параметров для фильтрации отображаемых учетных данных. Например, для списка нелицензированных пользователей (пользователей, которые были добавлены в Office 365, но еще не лицензированы для использования каких-либо служб) выполните указанную ниже команду.
  
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

Дополнительные сведения о дополнительных параметрах для фильтрации отображаемого набора учетных записей пользователей приведены в статье [Get – MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="view-a-specific-account"></a>Просмотр определенной учетной записи

Чтобы отобразить определенную учетную запись пользователя, введите учетную запись пользователя учетной записи пользователя, которая также называется именем участника-пользователя (UPN), удалите символы "_Лт_" и "_Гт_", а затем выполните следующую команду:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Просмотр некоторых учетных записей на основе общего свойства

Чтобы еще точнее отфильтровать список отображаемых учетных записей, можно использовать сочетание командлетов **Where-Object** и **Get-MsolUser**. Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который указывает оболочке PowerShell Office 365 для получения результатов одной команды и отправки их следующей команде. Ниже приведен пример команды, которая выводит только учетные записи, для которых не указано место использования:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).
    
- Найдите все учетные записи пользователей с незаданной областью использования ( **где-Object {$\_. UsageLocation-EQ $Null}** ). В фигурных скобках команда инструктирует Office 365 PowerShell, чтобы найти только те учетные записи, в которых свойство учетной записи пользователя UsageLocation ( ** $ \_. UsageLocation** ) не указан ( **-EQ $NULL** ).
    
Выходные данные должны выглядеть примерно следующим образом:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

**UsageLocation** — лишь одно из многих свойств, связанных с учетной записью пользователя. Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (*), чтобы отображать их все для конкретной учетной записи пользователя. Вот пример:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Например, **City** для этого списка — имя свойства, принадлежащего учетной записи пользователя. Это значит, что перечислить все учетные записи пользователей, проживающих в Лондоне, можно с помощью такой команды:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Для командлета **Where-Object** , показанного в этих примерах, используется синтаксис **Where-\_Object {$.** [имя свойства учетной записи пользователя] [оператор сравнения] оно **}**.  [оператор сравнения] имеет значение **-EQ** для Equals, **-Ne** для Not Equals, **-lt** для "больше чем", " **-gt** " для "больше чем", и других.  [Value] как правило, это строка (последовательность букв, цифр и других знаков), числовое значение или **$null** не указано. Для [](https://technet.microsoft.com/en-us/library/hh849715.aspx) получения дополнительных сведений см.
  
Вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:
  
```
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Просмотр дополнительных значений свойств для учетных записей

Командлет **Get – MsolUser** по умолчанию отображает три свойства учетных записей пользователей:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Если требуются дополнительные свойства, такие как отдел, с которым работает пользователь, и страна или регион, где пользователь использует службы Office 365, можно выполнить командлет **Get-MsolUser** в сочетании с командлетом **Select-Object** , чтобы указать список учетных записей пользователей. параметры. Вот пример:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).
    
- Отображение только имени, отдела и места использования учетной записи пользователя ( **Select-Object DisplayName, Department, UsageLocation** ).
    
Выходные данные должны выглядеть примерно следующим образом:
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

Командлет **Select – Object** позволяет выбирать и выбирать свойства, которые должна отображать команда. Чтобы просмотреть все свойства учетных записей пользователей, используйте подстановочный знак (*), чтобы отображать их все для конкретной учетной записи пользователя. Пример:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Чтобы еще точнее отфильтровать список отображаемых учетных записей, можно также использовать командлет **Where-Object**. Ниже приведен пример команды, которая выводит только те учетные записи пользователей, для которых не указано расположение использования.
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).
    
- Найдите все учетные записи пользователей с незаданной областью использования ( **где-Object {$\_. UsageLocation-EQ $Null}** ) и отправьте полученные сведения в следующую команду ( **|** ). В фигурных скобках команда предписывает PowerShell Office 365, чтобы найти только те учетные записи, в которых свойство учетной записи пользователя UsageLocation ( ** $ \_. UsageLocation** ) не указан ( **-EQ $NULL** ).
    
- Отображение только имени, отдела и места использования учетной записи пользователя ( **Select-Object DisplayName, Department, UsageLocation** ).
    
Выходные данные должны выглядеть примерно следующим образом:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Если вы используете синхронизацию службы каталогов для создания пользователей Office 365 и управления ими, вы можете отобразить локальную учетную запись, с которой был проецирован пользователь Office 365. Ниже предполагается, что Azure AD Connect настроен на использование привязки источника по умолчанию ObjectGUID (Дополнительные сведения о настройке привязки источника см. в статье [Azure AD Connect: концепция дизайна](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) и предполагается, что модуль Active Directory для PowerShell установлены (см. [инструменты RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a>См. также

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

