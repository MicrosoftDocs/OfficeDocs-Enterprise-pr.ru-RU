---
title: "Отключение доступа к службам с помощью Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Объясняет, как использовать Office 365 PowerShell для отключения доступа к службам Office 365 для пользователей в вашей организации."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Отключение доступа к службам с помощью Office 365 PowerShell

**Сводка:** Объясняет, как использовать Office 365 PowerShell для отключения доступа к службам Office 365 для пользователей в вашей организации.
  
Если учетная запись Office 365 назначена лицензия из плана лицензирования, служб Office 365 становятся доступными для пользователя из этой лицензии. Тем не менее можно управлять служб Office 365, которые могут иметь доступ этот пользователь. Например несмотря на то, что лицензия позволяет получить доступ к SharePoint Online, можно отключить доступ к нему. На самом деле Office 365 PowerShell можно использовать для отключения доступа к любой номер для служб:

- отдельная учетная запись;
    
- группа учетных записей;
    
- все учетные записи в организации.
    
## <a name="before-you-begin"></a>Перед началом работы
<a name="RTT"> </a>

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Командлет **Get-MsolAccountSku** используется для просмотра доступные планы лицензирования и служб Office 365, доступные в этих планах. Для получения дополнительных сведений см. [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Чтобы просмотреть до и после выполнения процедур, описанных в данном разделе увидеть [просмотреть сведения о лицензии и службы учетной записи с помощью Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- При использовании командлета **Get-MsolUser** без использования _всех_ параметров возвращаются только первой 500 учетных записей.
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a>Планирование конкретных служб Office 365 для конкретных пользователей для одной лицензирования
  
Чтобы отключить определенного набора служб Office 365 для пользователей из одного плана лицензирования, выполните следующие действия:
  
1. Выбор нежелательный служб в плане лицензирования, используя следующий синтаксис:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    В следующем примере создается объект **LicenseOptions** , который отключает службы Office Online и SharePoint Online в плане лицензирования с именем `litwareinc:ENTERPRISEPACK` (Office 365 для предприятий E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Используйте объект **LicenseOptions** из шага 1 на одного или нескольких пользователей.
    
  - Чтобы создать учетную запись, для которой отключены службы, используйте указанную ниже команду.
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    В следующем примере создается новая учетная запись для Allie Bellew, который назначает лицензии и отключает служб, описанных в шаге 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    Дополнительные сведения о создании учетных записей пользователей в Office 365 PowerShell можно [Создать учетные записи пользователей с Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Чтобы отключить службы для существующего лицензированного пользователя, выполните указанную ниже команду.
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    В этом примере показано, как отключить службы для пользователя BelindaN@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Для отключения служб, описанных в разделе шаг 1 для всех существующих лицензированных пользователей, укажите имя плана Office 365 с экрана в командлет **Get-MsolAccountSku** (например, **litwareinc: enterprisepack**) и затем выполните следующие команды:
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - Чтобы отключить службы для группы существующих пользователей, воспользуйтесь одним из указанных ниже методов для идентификации пользователей.
    
  - **Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    В следующем примере отключается службы для сотрудников отдела продаж в США.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Использование списка определенных учетных записей** Для этого выполните следующие действия:
    
1. Создайте текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    В этом примере в текстовом файле — C:\\Мои документы\\Accounts.txt.
    
2. Выполните следующую команду:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Для отключения служб Office 365 для пользователей во время при назначении их план лицензирования см [запрещать доступ к службам при назначении лицензии пользователя](disable-access-to-services-while-assigning-user-licenses.md).
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a>Конкретных служб Office 365 для пользователей из всех планы лицензирования
  
Чтобы отключить служб Office 365 для пользователей в все доступные планы лицензирования, выполните следующие действия:
  
1. Скопируйте и вставьте сценарий в Блокнот.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. В своей среде настройте указанные ниже значения.
    
  -  _<UndesirableService>_В этом примере мы будем использовать Office Online и SharePoint Online.
    
  -  _<Account>_В этом примере мы будем использовать belindan@litwareinc.com.
    
    Измененный сценарий выглядит указанным ниже образом.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. Сохраните сценарий в `RemoveO365Services.ps1` в папке, где можно найти. В данном примере мы будем сохраните файл в `C:\\O365 Scripts`.
    
4. Запустите сценарий в Office 365 PowerShell с помощью следующей команды.
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Для отмены эффекты любого из этих процедур (то есть, чтобы повторно включить отключенные службы), снова выполнить процедуру, но использовать значение `$null` для параметра _DisabledPlans_ .
  
[В начало](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a>Все службы Office 365 для всех пользователей для одного плана лицензирования
 
Чтобы отключить все службы Office 365 для всех пользователей в определенных плана лицензирования, укажите имя плана лицензирования для $acctSKU (например, **litwareinc: enterprisepack**) и затем выполните следующие команды в окне командной строки PowerShell:

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

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
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Новый MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [SET-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

