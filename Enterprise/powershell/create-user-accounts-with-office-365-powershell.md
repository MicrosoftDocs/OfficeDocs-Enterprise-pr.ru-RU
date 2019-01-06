---
title: Создание учетных записей пользователей с помощью PowerShell в Office 365
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Сведения о том, как с помощью PowerShell в Office 365 создавать учетные записи пользователей в Office 365:.
ms.openlocfilehash: 902f44dd4fc42d8f29ce92748cbbf1ce03c6615b
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730314"
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Создание учетных записей пользователей с помощью PowerShell в Office 365

**Сводка.** Узнайте, как создавать учетные записи пользователей в Office 365, используя PowerShell.
  
С помощью PowerShell в Office 365 можно эффективно создавать учетные записи пользователей, особенно если нужно создать сразу несколько. При создании учетных записей пользователей в PowerShell в Office 365 указываются определенные свойства. Одни из них обязательны, другие  нет. Все свойства важны. Они описаны в приведенной ниже таблице.
  
|**Имя свойства**|**Обязательный?**|**Описание**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Да  <br/> |Это отображаемое имя, которое используется в службах Office 365:. Например, Caleb Sills.  <br/> |
|**UserPrincipalName** <br/> |Да  <br/> |Это имя учетной записи, которое используется для входа в службы Office 365:. Например, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |Нет  <br/> ||
|**LastName** <br/> |Нет  <br/> ||
|**LicenseAssignment** <br/> |Нет  <br/> |Это план лицензирования (также называемый планом Office 365 или SKU), согласно которому учетной записи пользователя назначается доступная лицензия. Лицензия определяет, какие службы Office 365 доступны учетной записи пользователя. Создавая учетную запись, пользователю не обязательно назначать лицензию, но она необходима для доступа к службам Office 365. Лицензию необходимо добавить в течение 30 дней после создания учетной записи пользователя. |
|**Password** <br/> |Нет  <br/> | Если не задать пароль, для учетной записи пользователя назначается случайный пароль, отображающийся в результатах выполнения команды. Если вы решили задать пароль самостоятельно, он должен содержать от 8 до 16 текстовых знаков ASCII любых трех типов из указанных далее: строчные буквы, прописные буквы, числа и символы. <br/> |
|**UsageLocation** <br/> |Нет  <br/> |Это действительный код страны по стандарту ISO 3166-1 alpha-2 (например, US для США и FR для Франции). Важно указать это значение, так как некоторые службы Office 365 недоступны в определенных странах. Следовательно, если это значение не указано, то учетной записи пользователя не удастся назначить лицензию. Дополнительные сведения см. в статье [О лицензионных ограничениях](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

После подключения используйте следующий синтаксис, чтобы создать учетную запись:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

В этом примере создается учетная запись пользователя Caleb Sills из Соединенных Штатов:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Создание одной учетной записи пользователя

Чтобы создать одну учетную запись, используйте следующий синтаксис:
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

Чтобы предоставить список доступных имен плана лицензирования, используйте следующую команду:

````
Get-MsolAccountSku
````

Этот пример кода создает учетную запись для пользователя в США с именем Caleb Sills и назначает для него лицензию согласно плану лицензирования `contoso:ENTERPRISEPACK` (Office 365 корпоративный E3).
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Создание нескольких учетных записей пользователей

1. Создайте CSV-файл, который содержит обязательные сведения об учетных записях пользователей. Пример:
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>Имена столбцов и их порядок в первой строке CSV-файла произвольны, но остальные данные в файле должны соответствовать порядку названий столбцов. Используйте названия столбцов в качестве значений параметров в команде PowerShell для Office 365.
    
2. Используйте указанный ниже синтаксис.
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

Этот пример кода создает учетные записи пользователей на основе файла NewAccounts.csv (C:\My Documents\NewAccounts.csv) и записывает результаты в файл NewAccountResults.csv (C:\My Documents\NewAccountResults.csv).
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Результаты можно просмотреть в выходном файле. Мы не указывали пароли, поэтому в выходном файле отображаются случайные значения, созданные Office 365.
    
## <a name="see-also"></a>См. также

[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
