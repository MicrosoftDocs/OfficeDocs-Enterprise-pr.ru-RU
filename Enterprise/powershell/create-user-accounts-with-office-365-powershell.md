---
title: "Создание учетных записей пользователей с помощью PowerShell в Office 365"
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
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "Сведения о том, как с помощью PowerShell в Office 365 создавать учетные записи пользователей в Office 365:."
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Создание учетных записей пользователей с помощью PowerShell в Office 365

**Сводка:** Сведения об использовании Office 365 PowerShell для создания учетных записей пользователей в Office 365.
  
С помощью PowerShell в Office 365 можно эффективно создавать учетные записи пользователей, особенно если нужно создать сразу несколько. При создании учетных записей пользователей в PowerShell в Office 365 указываются определенные свойства. Одни из них обязательны, другие  нет. Все свойства важны. Они описаны в приведенной ниже таблице.
  
****

|**Имя свойства**|**Обязательное?**|**Описание**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Да  <br/> |Это отображаемое имя, которое используется в службах Office 365:. Например, Caleb Sills.  <br/> |
|**UserPrincipalName** <br/> |Да  <br/> |Это имя учетной записи, которое используется для входа в службы Office 365:. Например, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |Нет  <br/> ||
|**LastName** <br/> |Нет  <br/> ||
|**LicenseAssignment** <br/> |Нет  <br/> |Это план лицензирования (также известный как план Office 365: или SKU), согласно которому для учетной записи пользователя назначается доступная лицензия. Лицензия определяет службы Office 365:, доступные для учетной записи пользователя. При создании учетной записи пользователя для него не обязательно назначать лицензию, но последняя необходима для доступа к службам Office 365:. Лицензию требуется добавить в течение 30 дней после создания учетной записи пользователя.<br/> Командлет **Get-MsolAccountSku** используется для просмотра планы лицензирования ( **AccountSkuId** ) и доступных лицензий в организации. Для получения дополнительных сведений см. [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).<br/> |
|**Password** <br/> |Нет  <br/> | Если не задать пароль, для учетной записи пользователя назначается случайный пароль, отображающийся в результатах выполнения команды. Если вы решили задать пароль самостоятельно, он должен быть достаточно сложным. Для этого: <br/>  Требуется указать от 8 до 16 текстовых знаков ASCII. <br/>  Знаки должны быть любого из четырех типов: строчные буквы, прописные буквы, числа и символы. <br/> |
|**UsageLocation** <br/> |Нет  <br/> |Это допустимый код страны согласно ISO 3166-1 alpha-2 (например, US для США и FR для Франции). Важно указать это значение, так как некоторые службы Office 365: недоступны в определенных странах. Следовательно, вы не сможете назначить лицензию для учетной записи пользователя, если для нее не настроено это значение. Дополнительные сведения см. в статье [О лицензионных ограничениях](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   
## <a name="before-you-begin"></a>Приступая к работе

Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>Создание одной учетной записи пользователя с помощью PowerShell в Office 365

Чтобы создать одну учетную запись, используйте следующий синтаксис:
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

Этот пример кода создает учетную запись для пользователя в США с именем Caleb Sills и назначает для него лицензию согласно плану лицензирования  `contoso:ENTERPRISEPACK` (Office 365 для предприятий E3).
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>Создание нескольких учетных записей пользователей с помощью PowerShell в Office 365

1. Создайте CSV-файл, который содержит требуемые сведения об учетных записях пользователей. Например:
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>Имена столбцов и их порядок в первой строке в CSV-файле произвольных, но убедитесь, что данные в остальные файла совпадает с порядком имена столбцов и использовать имена столбцов для значений параметров в Office 365 PowerShell команду.
    
2. Используйте следующий синтаксис:
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

Этот пример кода создает учетные записи пользователей на основе файла NewAccounts.csv (C:\My Documents\NewAccounts.csv) и записывает результаты в файл NewAccountResults.csv (C:\My Documents\NewAccountResults.csv).
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Результаты можно просмотреть в выходном файле. Мы не указывали пароли, поэтому в выходном файле отображаются случайные пароли.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>Создание учетных записей пользователей с помощью модуля Azure Active Directory PowerShell 2

Чтобы использовать командлет **New-AzureADUser** из модуля Azure Active Directory версии 2 PowerShell, необходимо сначала подключиться к своей подписке. Инструкции в разделе [подключение с помощью модуля Azure Active Directory версии 2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
После подключения используйте следующий синтаксис, чтобы создать учетную запись:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

В этом примере создается учетная запись пользователя Caleb Sills из Соединенных Штатов:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>See also

Разделах эти дополнительные сведения об управлении пользователями с помощью Office 365 PowerShell:
  
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Блокировка учетных записей пользователей с помощью PowerShell в Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в следующих статьях:
  
- [Export-Csv](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv);
    
- [Новый MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Новый AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

