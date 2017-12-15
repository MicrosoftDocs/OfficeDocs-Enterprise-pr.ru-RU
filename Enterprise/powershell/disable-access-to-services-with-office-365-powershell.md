---
title: "Отключение доступа к службам с помощью Office 365 PowerShell"
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "В данной статье описывается использование Office 365 PowerShell для добавления или удаления доступа к службам Office 365 для пользователей в вашей организации."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Отключение доступа к службам с помощью Office 365 PowerShell

**Сводка:** В данной статье описывается использование Office 365 PowerShell для добавления или удаления доступа к службам Office 365 для пользователей в вашей организации.
  
Если учетная запись Office 365 назначена лицензия из плана лицензирования, служб Office 365 становятся доступными для пользователя из этой лицензии. Тем не менее можно управлять служб Office 365, которые могут иметь доступ этот пользователь. Например несмотря на то, что лицензия позволяет получить доступ к SharePoint Online, можно отключить доступ к нему. На самом деле Office 365 PowerShell можно использовать для отключения доступа к любой номер для служб:
- отдельная учетная запись;
    
- группа учетных записей;
    
- все учетные записи в организации.
    
 **Содержимое:** [Краткого (инструкции без объяснения)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [Длинные версии (инструкции с подробными пояснениями)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [См. также:](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>Перед началом работы
<a name="RTT"> </a>

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Командлет **Get-MsolAccountSku** используется для просмотра доступные планы лицензирования и служб Office 365, доступные в этих планах. Для получения дополнительных сведений см.[Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Чтобы просмотреть до и после выполнения процедур, описанных в данном разделе увидеть [просмотреть сведения о лицензии и службы учетной записи с помощью Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Если использовать командлет **Get-MsolUser** без параметра _All_, возвращаются только первые 500 учетных записей.
    
## <a name="the-short-version-instructions-without-explanations"></a>Краткая версия (инструкции без пояснений)
<a name="ShortVersion"> </a>

В этом разделе процедуры представлены без лишних слов и объяснений. Если у вас возникнут вопросы или вам потребуются дополнительные сведения, вы можете прочитать остальные разделы статьи.
  
Чтобы отключить служб Office 365 для пользователей из одного плана лицензирования, выполните следующие действия:
  
1. Выбор нежелательный служб в плане лицензирования, используя следующий синтаксис:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    В этом примере создается объект **LicenseOptions** , который отключает службы Office Online и SharePoint Online в плане лицензирования с именем `litwareinc:ENTERPRISEPACK` (Office 365 для предприятий E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Используйте объект **LicenseOptions** из шага 1 на одного или нескольких пользователей.
    
  - Чтобы создать учетную запись, для которой отключены службы, используйте указанную ниже команду.
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    В этом примере показано, как создать учетную запись для пользователя Allie Bellew, назначить лицензию и отключить службы, описанные в действии 1.
    
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

  - Для отключения служб, описанных в разделе шаг 1 для всех существующих лицензированных пользователей, укажите имя плана Office 365 с экрана в командлет **Get-MsolAccountSku** (например, **litwareinc: enterprisepack** ) и затем выполните следующие команды:
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - Чтобы отключить службы для группы существующих пользователей, воспользуйтесь одним из указанных ниже методов для идентификации пользователей.
    
  - **Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    В этом примере показано, как отключить службы для пользователей из отдела продаж в США.
    
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
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Для отключения служб Office 365 для пользователей во время при назначении их план лицензирования см [запрещать доступ к службам при назначении лицензии пользователя](disable-access-to-services-while-assigning-user-licenses.md).
  
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

3. Сохраните сценарий в `RemoveO365Services.ps1` в папке, где можно найти. В данном примере мы будем сохраните файл в " `C:\\O365 Scripts`«.
    
4. Запустите сценарий в Office 365 PowerShell с помощью следующей команды.
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Для отмены эффекты любого из этих процедур (то есть, чтобы повторно включить отключенные службы), снова выполнить процедуру, но использовать значение `$null` для параметра _DisabledPlans_ .
  
[В начало](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>Подробная версия (инструкции с подробными пояснениями)
<a name="LongVersion"> </a>

По умолчанию все службы включены при использовании функции лицензии с помощью Office 365 PowerShell. И часто это хорошо: это означает, что вы можете быстро и легко назначение лицензий пользователям без указания включения каждой службы по пути.
  
Другой стороны, который, тем не менее, верно, кроме того, можно ограничить список доступных служб некоторым пользователям; Например может быть некоторые пользователи должны иметь доступ к Office профессиональный плюс, Скайп для бизнеса в Интернет и Exchange Online, но те же пользователи не следует иметь доступ к SharePoint Online или Office Online. Можно ограничить учетных записей, образом? Как оказывается, вы можете. Чтобы объяснить, как это работает, давайте два подхода к решению этой проблемы:
  
1. Назначение пользователю лицензии Office 365, которая автоматически включает все службы.
    
2. Выполнение пары команд Office 365 PowerShell, отключающих указанные службы для этого пользователя.
    
Мы проведена шаг 1: наших пользователей (Светлане Коноваловой) имеет лицензии Office 365, который предоставляет ему с доступом к службам Office 365. Тем не менее, его нужно изменить учетную запись Светлане таким образом, чтобы она не имеет доступа к SharePoint Online ( `SHAREPOINTENTERPRISE`) или на узле Office Online ( `SHAREPOINTWAC`). Но как мы должны сделать это?
  
Вот как. Начинается с мы будем использовать командлет **New-MsolLicenseOptions** для создания объекта **LicenseOption** , который содержит службы, которые необходимо отключить. В случае Светлане его нужно отключить `SHAREPOINTENTERPRISE` и `SHAREPOINTWAC`, поэтому мы используем эту команду:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

Видите, как это работает? Вы задаете план лицензирования ( `litwareinc:ENTERPRISEPACK`) и затем указываете каждую из служб, которые нужно отключить, разделяя их запятыми.
  
> [!NOTE]
> Убедитесь, что ваш новый объект **LicenseOption** сохранить в переменной. В предыдущем примере мы использовали `$x`, хотя можно использовать любое допустимое имя переменной Windows PowerShell. 
  
На этом этапе можно использовать следующую команду для отключения Светлане доступ две службы:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Ничего не слишком фигурном здесь, либо: мы просто вызовите командлет **Set-MsolUserLicense** и включить параметр _LicenseOptions_ , а также переменной ( `$x`) содержащий планов, его нужно отключить. И что мы видим теперь Если взглянуть на информацию о лицензии Светлане, выполнив команду: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Мы увидеть следующее:
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

Здорово, правда? И, конечно, то же самое можно делать к нескольким пользователям при желании. Например эти команды отключить же две службы для всех наших лицензированных пользователей. Укажите имя плана Office 365 с экрана в командлет **Get-MsolAccountSku** (например, **litwareinc: enterprisepack** ) и затем использовать их для работы.
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

Помните, что Светлане по-прежнему имеет действительной лицензии Office 365; он является теперь у нее есть доступ к службам меньшего числа. Прежде чем мы отключили две службы, Светлане имел доступ к каналы новостей, OneDrive и SharePoint Online сайтов:
  
![Пользователь с доступом к SharePoint.](images/o365_powershell_with_sharepoint.png)
  
Теперь эти возможности ей недоступны.
  
![Пользователь без доступа к SharePoint.](images/o365_powershell_without_sharepoint.png)
  
Мы хотели сделать именно это.
  
И что делать, если мы наших виду впоследствии изменить: можно ли включить данные службы? Вы уверены, что Да. Чтобы повторно включить все службы для пользователя, используйте следующую команду для создания следующих объектов **LicenseOption** :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Что такое этой команды? Чтобы начать с помощью Windows PowerShell константу `$null` означает, что «нет». (Или немного больше технические языке, это означает «нулевое значение».) Как вы помните, когда мы используем командлет **New-MsolLicenseOptions** , у нас есть укажите службы, мы должны отключено. В этом случае мы не должен любую из служб, чтобы отключить. Вы уверены, что мы могли бы использовать команду следующим образом, где мы не задано значение для параметра _DisabledPlans_ команду, которая может быть:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

Тем не менее, которые не будут работать. Вместо этого он создает сообщение об ошибке:
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
К счастью для нас, установка для параметра значения `$null` работы:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Это просто значит, что при выполнении командлета **Set-MsolUserLicense** мы указываем **Set-MsolUserLicense** , что мы не на какие-либо отключенные службы.
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Само собой понятно, что если ни одна из служб не отключена, то все службы включены.
  
Теперь, когда вы понимаете, как это работает, давайте показано, как выдавать лицензии и отключение указанных служб и всех с помощью одной команды. Звучит довольно Впечатляет, но честно, в этом нет ничего не к нему: только что включают _Параметры AddLicenses_ и _LicenseOptions_ используются в одной команде. Другими словами сначала создайте объект **LicenseOption** :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

И затем, как указывалось ранее, использовать _Параметры AddLicenses_ и _LicenseOptions_ используются в команде:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

Что команда будет выдавать Светлане Коноваловой новую лицензию, но лицензии в какие Скайп для бизнеса в Интернет ( `SHAREPOINTWAC`) и SharePoint Online ( `SHAREPOINTENTERPRISE`) являются оба отключены.
  
[В начало](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?
<a name="LongVersion"> </a>

||
|:-----|
|![Короткие значок обучения LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Создать в Office 365?**         Обнаружение Бесплатные курсы видео для **ИТ-специалистов и администраторов Office 365**, с LinkedIn обучения. |
   
## <a name="see-also"></a>See also
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
    
- [Новый MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [SET-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[В начало](disable-access-to-services-with-office-365-powershell.md#RTT)
  

