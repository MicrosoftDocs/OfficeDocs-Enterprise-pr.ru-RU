---
title: Отключение доступа к службам с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Отключение доступа к службам Office 365 для пользователей с помощью PowerShell в Office 365.
ms.openlocfilehash: 711f48dd2caad6fc2b438010405b126be203bd54
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257604"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Отключение доступа к службам с помощью Office 365 PowerShell

Когда учетной записи Office 365 назначена лицензия в плане лицензирования, службы Office 365 предоставляются пользователю из этой лицензии. Тем не менее, вы можете управлять службами Office 365, к которым у пользователя есть доступ. Например, несмотря на то, что лицензия разрешает доступ к службе SharePoint Online, вы можете отключить доступ к ней. С помощью PowerShell можно отключить доступ к любому числу служб для определенного плана лицензирования:

- отдельная учетная запись;
    
- группа учетных записей;
    
- все учетные записи в организации.

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Затем используйте эту команду для просмотра доступных планов лицензирования, известных также как Аккаунтскуидс:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core не поддерживает модуль Microsoft Azure Active Directory для модуля Windows PowerShell и командлеты с **MSOL** в имени. Чтобы продолжить использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>

Дополнительные сведения см. [в статье Просмотр лицензий и служб с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Чтобы просмотреть результаты процедуры, описанные в этом разделе, в статье [Просмотр сведений о лицензиях и службах для учетной записи с помощью Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
Кроме того, вы можете воспользоваться сценарием PowerShell, который автоматизирует выполнение процедур, описанных в этой статье. В частности, скрипт позволяет просматривать и отключать службы в организации Office 365, в том числе Sway. Дополнительные сведения см. в статье [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Отключение определенных служб Office 365 для определенных пользователей по определенному плану лицензирования
  
Чтобы отключить определенный набор служб Office 365 для пользователей по определенному плану лицензирования, выполните указанные ниже действия.
  
1. Определите нежелательные службы в плане лицензирования, используя следующий синтаксис:
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  В следующем примере создается объект **LicenseOptions** , который отключает службы Office и SharePoint Online в плане лицензирования под названием `litwareinc:ENTERPRISEPACK` (Office 365 корпоративный E3).
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Используйте объект **LicenseOptions** из действия 1 для одного или нескольких пользователей.
    
  - Чтобы создать учетную запись, для которой отключены службы, используйте указанную ниже команду.
    
  ```powershell
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  В следующем примере создается новая учетная запись для (Allie bellew), которая назначает лицензию и отключает службы, описанные в шаге 1.
    
  ```powershell
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  Более подробную информацию о создании учетных записей пользователей в Office 365 PowerShell можно узнать в статье [Создание учетных записей пользователей с помощью office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Чтобы отключить службы для существующего лицензированного пользователя, выполните указанную ниже команду.
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  В этом примере показано, как отключить службы для пользователя BelindaN@litwareinc.com.
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Чтобы отключить службы, описанные в шаге 1, для всех существующих лицензированных пользователей, укажите имя плана Office 365 из отображения командлета **Get-MsolAccountSku** (например, **litwareinc: ENTERPRISEPACK**), а затем выполните следующие команды:
    
  ```powershell
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  Если вы используете командлет **Get – MsolUser** без параметра _ALL_ , возвращаются только первые 500 учетных записей пользователей.


  - Чтобы отключить службы для группы существующих пользователей, воспользуйтесь одним из указанных ниже методов для идентификации пользователей.
    
  - **Фильтрация учетных записей на основе существующего атрибута учетной записи** Для этого используйте следующий синтаксис:
    
  ```powershell
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  В следующем примере отключаются службы для пользователей в отделе продаж в США.
    
  ```powershell
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Использование списка определенных учетных записей** Для этого выполните указанные ниже действия.
    
1. Создайте текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  В этом примере текстовый файл имеет значение C:\\мои документы\\Accounts. txt.
    
2. Выполните следующую команду:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Если вы хотите отключить доступ к службам для нескольких планов лицензирования, повторите указанные выше инструкции для каждого плана лицензирования, убедившись в том, что:

- Учетным записям пользователей назначен план лицензирования.
- Службы, которые необходимо отключить, доступны в плане лицензирования.

Чтобы отключить службы Office 365 для пользователей при назначении их плану лицензирования, ознакомьтесь со статьей [Отключение доступа к службам при назначении пользовательских лицензий](disable-access-to-services-while-assigning-user-licenses.md).


## <a name="new-to-office-365"></a>Никогда не работали с Office 365?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>См. также
<a name="SeeAlso"> </a>

Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:
  
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Блокировка учетных записей пользователей с помощью PowerShell в Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Создание учетных записей пользователей с помощью PowerShell в Office 365](create-user-accounts-with-office-365-powershell.md)
    
