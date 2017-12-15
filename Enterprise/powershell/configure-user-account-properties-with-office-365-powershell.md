---
title: "Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365"
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
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Сводка. Сведения о том, как с помощью PowerShell в Office 365 настроить свойства одной или нескольких учетных записей пользователей в клиенте Office 365:."
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365

 **Сводка:** Использование Office 365 PowerShell для настройки свойств из одного или нескольких учетных записей пользователей в клиент Office 365.
  
Хотя настраивать свойства учетных записей пользователей для клиента Office 365: можно и в Центре администрирования Office 365:, PowerShell в Office 365 позволяет выполнять задачи, не доступные в Центре администрирования Office 365:.
  
## <a name="before-you-begin"></a>Приступая к работе

Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="change-properties-for-a-specific-user-account"></a>Изменение свойств для определенной учетной записи пользователя

Чтобы настроить свойства для определенной учетной записи пользователя, используйте командлет [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) и укажите свойства, которые нужно задать или изменить. Приведенный ниже пример команды меняет расположение использования для пользователя Belinda Newman, задавая Францию.
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Параметр **-UserPrincipalName** позволяет определить учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Те из них, которые чаще всего используются, представлены ниже.
  
- -Город "\<название города >»
    
- -Страна "\<название страны >»
    
- -Department "\<имя отдела >»
    
- -DisplayName "\<полное имя пользователя >»
    
- -Факс "\<номер факса >»
    
- -FirstName "\<имя пользователя >»
    
- -LastName "\<Фамилия пользователя >»
    
- -MobilePhone "\<номер мобильного телефона >»
    
- — Office "\<расположение комнаты >»
    
- -PhoneNumber "\<office номер телефона >»
    
- -PostalCode "\<почтовый индекс >»
    
- -PreferredLanguage "\<язык >»
    
- -Состояние "\<имя состояния >»
    
- Улица-"\<почтовый адрес >»
    
- -Title "\<имя заголовка >»
    
- -UsageLocation "\<2-символьный код страны или региона >»
    
    Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).
    
Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).
  
Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).
    
- Сортировка списка имена участника-пользователя ( **UserPrincipalName Sort-Object** ) и отправьте его в следующей команде ( **|** ).
    
- Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).
    
- Отобразить их на одном экране ( **More** ).
    
Эта команда выводит список всех учетных записей. Если вы хотите отобразить имя участника-пользователя для учетной записи на основании его отображения name (имя и фамилию), заполните поля в переменной **$userName** ниже (удаление \< и > символов), и затем выполните следующие команды:
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>Изменение свойств для всех учетных записей пользователей

Чтобы изменить свойства для всех пользователей, можно использовать сочетание командлетов **Get-MsolUser** и **Set-MsolUser**. В следующем примере место работы всех пользователей меняется на Францию:
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).
    
- Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Изменение свойств для определенного набора учетных записей пользователей

Сочетание командлетов **Get-MsolUser**, **Where-Object** и **Set-MsolUser** позволит изменить свойства для определенного набора учетных записей пользователей. Пример кода, приведенный ниже, заменяет текущее расположение использования для всех пользователей в отделе Accounting (бухгалтерского учета) на Францию.
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).
    
- Найти все учетные записи пользователей, которые имеют отдела свойство присвоено значение «Accounting» ( **Where-Object {$_. Отдел - eq «Учет»}** ) и отправлять полученные сведения к следующей команде ( **|** ).
    
- Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).
    
- Отобразить их на одном экране ( **More** ).
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Как настроить свойства учетных записей пользователей с помощью модуля PowerShell для Azure Active Directory 2

Чтобы настроить свойства для учетных записей пользователей с помощью модуля Azure Active Directory версии 2 PowerShell, с помощью командлета [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) и укажите свойства для задания или изменения. Но для начала необходимо подключиться к своей подписке. Инструкции в разделе [подключение с помощью модуля Azure Active Directory версии 2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="change-properties-for-a-specific-user-account"></a>Изменение свойств для определенной учетной записи пользователя

Этот пример команды заменяет текущее расположение использования для пользователя Belinda Newman на Францию:
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Параметр **-ObjectID** позволяет определить учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Те из них, которые чаще всего используются, представлены ниже.
  
- -Department "\<имя отдела >»
    
- -DisplayName "\<полное имя пользователя >»
    
- -FacsimilieTelephoneNumber "\<номер факса >»
    
- -GivenName "\<имя пользователя >»
    
- -Фамилия "\<Фамилия пользователя >»
    
- -Мобильных устройств "\<номер мобильного телефона >»
    
- — Название должности "\<должность >»
    
- -PreferredLanguage "\<язык >»
    
- Улица-"\<почтовый адрес >»
    
- -Город "\<название города >»
    
- -Состояние "\<имя состояния >»
    
- -PostalCode "\<почтовый индекс >»
    
- -Страна "\<название страны >»
    
- -TelephoneNumber "\<office номер телефона >»
    
- -UsageLocation "\<2-символьный код страны или региона >»
    
    Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).
    
Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).
  
Для отображения имени участника-пользователя для учетные записи пользователей, выполните следующую команду.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).
    
- Сортировка списка имена участника-пользователя ( **UserPrincipalName Sort-Object** ) и отправьте его в следующей команде ( **|** ).
    
- Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).
- Отобразить их на одном экране ( **More** ).
    
Эта команда выводит список всех учетных записей. Если вы хотите отобразить имя участника-пользователя для учетной записи на основании его отображения name (имя и фамилию), заполните поля в переменной **$userName** ниже (удаление \< и > символов), и затем выполните следующие команды:
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Изменение свойств для всех учетных записей пользователей

Чтобы изменить свойства для всех пользователей, примените сочетание командлетов **Get-AzureADUser** и **Set-AzureADUser**. Следующий пример заменяет текущее расположение использования для всех пользователей на Францию:
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).
    
- Задать Францию в качестве расположения пользователя ( **Set-AzureADUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Изменение свойств для определенного набора учетных записей пользователей

Чтобы изменить свойства для определенного набора учетная запись пользователя, можно использовать сочетание командлеты **Get-AzureADUser**, **где**и **Set-AzureADUser** . В следующем примере изменяется местоположение об использовании для всех пользователей в бухгалтерии для Франции:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).
    
- Найти все учетные записи пользователей, которые имеют свойство отдела присвоено значение «Accounting» ( **где {$_. Отдел - eq «Учет»}** ) и отправлять полученные сведения к следующей команде ( **|** ).
    
- Задать Францию в качестве расположения пользователя ( **Set-AzureADUser -UsageLocation "FR"** ).
    
## <a name="see-also"></a>See also

#### 

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

