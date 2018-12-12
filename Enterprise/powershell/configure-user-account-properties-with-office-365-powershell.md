---
title: Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Сводка. Сведения о том, как с помощью PowerShell в Office 365 настроить свойства одной или нескольких учетных записей пользователей в клиенте Office 365:.
ms.openlocfilehash: 60b3c1d91df0cb28f19f60a285093de7337904a9
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
ms.locfileid: "17552692"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365

 **Сводка.** Настраивайте свойства учетных записей пользователей в клиенте Office 365, используя PowerShell для Office 365.
  
Хотя настраивать свойства учетных записей пользователей для клиента Office 365: можно и в Центре администрирования Office 365:, PowerShell в Office 365 позволяет выполнять задачи, не доступные в Центре администрирования Office 365:.
  
## <a name="before-you-begin"></a>Перед началом работы

Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="change-properties-for-a-specific-user-account"></a>Изменение свойств для определенной учетной записи пользователя

Чтобы настроить свойства для определенной учетной записи пользователя, используйте командлет [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) и укажите свойства, которые нужно задать или изменить. Приведенный ниже пример команды меняет расположение использования для пользователя Belinda Newman, задавая Францию.
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Параметр **-UserPrincipalName** позволяет определить учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Те из них, которые чаще всего используются, представлены ниже.
  
- -City "\<название города>"
    
- -Country "\<название страны>"
    
- -Department "\<название отдела>"
    
- -DisplayName "\<полное имя пользователя>"
    
- -Fax "\<номер факса>"
    
- -FirstName "\<имя пользователя>"
    
- -LastName "\<фамилия пользователя>"
    
- -MobilePhone "\<номер мобильного телефона>"
    
- -Office "\<адрес офиса>"
    
- -PhoneNumber "\<номер телефона офиса>"
    
- -PostalCode "\<почтовый индекс>"
    
- -PreferredLanguage "\<язык>"
    
- -State "\<название штата>"
    
- -StreetAddress "\<почтовый адрес>"
    
- -Title "\<должность>"
    
- -UsageLocation "\<2-значный код страны или региона>"
    
    Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).
    
Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).
  
Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).
    
- Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).
    
- Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).
    
- Отобразить их на одном экране ( **More** ).
    
Эта команда вернет все учетные записи. Если нужно отобразить имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), введите переменную **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:
  
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
  
- Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).
    
- Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Изменение свойств для определенного набора учетных записей пользователей

Сочетание командлетов **Get-MsolUser**, **Where-Object** и **Set-MsolUser** позволит изменить свойства для определенного набора учетных записей пользователей. Пример кода, приведенный ниже, заменяет текущее расположение использования для всех пользователей в отделе Accounting (бухгалтерского учета) на Францию.
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).
    
- Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where-Object {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).
    
- Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).
    
- Отобразить их на одном экране ( **More** ).
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Как настроить свойства учетных записей пользователей с помощью модуля PowerShell для Azure Active Directory 2

Чтобы настроить свойства учетных записей пользователей с помощью модуля Azure Active Directory 2 для PowerShell, выполните командлет [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0), указав свойства, которые нужно задать или изменить. Но сначала подключитесь к своей подписке ([инструкции](https://go.microsoft.com/fwlink/?linkid=842218)).
  
### <a name="change-properties-for-a-specific-user-account"></a>Изменение свойств для определенной учетной записи пользователя

Этот пример команды заменяет текущее расположение использования для пользователя Belinda Newman на Францию:
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Параметр **-ObjectID** позволяет определить учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Те из них, которые чаще всего используются, представлены ниже.
  
- -Department "\<название отдела>"
    
- -DisplayName "\<полное имя пользователя>"
    
- -FacsimilieTelephoneNumber "\<номер факса>"
    
- -GivenName "\<имя пользователя>"
    
- -Surname "\<фамилия пользователя>"
    
- -Mobile "\<номер мобильного телефона>"
    
- -JobTitle "\<должность>"
    
- -PreferredLanguage "\<язык>"
    
- -StreetAddress "\<почтовый адрес>"
    
- -City "\<название города>"
    
- -State "\<название штата>"
    
- -PostalCode "\<почтовый индекс>"
    
- -Country "\<название страны>"
    
- -TelephoneNumber "\<номер рабочего телефона>"
    
- -UsageLocation "\<2-значный код страны или региона>"
    
    Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).
    
Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).
  
Чтобы отобразить имя участника-пользователя для учетных записей пользователей, выполните следующую команду.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Эта команда указывает PowerShell в Office 365 сделать следующее:
  
- Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).
    
- Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).
    
- Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).
- Отобразить их на одном экране ( **More** ).
    
Эта команда вернет все учетные записи. Если нужно отобразить имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), введите переменную **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:
  
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

Эта команда дает инструкцию PowerShell для Office 365:
  
- Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).
    
- Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Изменение свойств определенной части учетных записей пользователей

Сочетание командлетов **Get-AzureADUser**, **Where** и **Set-AzureADUser** позволит изменить свойства определенной части учетных записей пользователей. Следующая команда заменяет расположение всех пользователей в отделе Accounting на Францию:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Эта команда дает инструкцию PowerShell для Office 365:
  
- Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).
    
- Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).
    
- Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).
    
## <a name="see-also"></a>См. также

#### 

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

