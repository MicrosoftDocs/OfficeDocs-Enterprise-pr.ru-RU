---
title: "Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365"
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
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей."
ms.openlocfilehash: 688e2775e7a028cd9dbe0c8ea27a7f3a453b5279
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365

**Сводка:**  В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.
  
Лицензирование учетных записей пользователей в Office 365 важна, так как пользователи не могут использовать какие-либо службы Office 365, пока не лицензированных своей учетной записи. Office 365 PowerShell можно использовать для эффективного назначения лицензий нелицензированных учетным записям, особенно нескольких учетных записей. 

## <a name="before-you-begin"></a>Перед началом работы
<a name="RTT"> </a>

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Командлет **Get-MsolAccountSku** используется для просмотра доступных планы лицензирования и число доступных лицензий в каждом плане в вашей организации. Число доступных лицензий в каждом плане — **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Чтобы найти нелицензированных учетные записи в вашей организации, выполните команду`Get-MsolUser -All -UnlicensedUsersOnly`
    
- Лицензии можно назначить только учетные записи пользователей, которые имеют свойство **UsageLocation** , равное допустимый код страны альфа-2 3166-1 ISO. Например, "мне НРАВИТСЯ" для США и FR для Франции. Некоторые службы Office 365 не доступны в некоторых странах. Для получения дополнительных сведений см [об ограничениях лицензии](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Чтобы найти учетные записи, которые не имеют значений **UsageLocation** , выполните команду `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Чтобы задать значение **UsageLocation** учетную запись, используйте следующий синтаксис `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Например `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- При использовании командлета **Get-MsolUser** без использования `-All` для параметра возвращаются только первые 500 учетных записей.
    
## <a name="the-short-version-instructions-without-explanations"></a>Краткая версия (инструкции без пояснений)
<a name="ShortVersion"> </a>

В этом разделе представлены процедуры без подробное объяснение. Если есть вопросы или для получения дополнительных сведений можно прочитать остальной части раздела.
  
Чтобы назначить лицензии пользователя, используйте следующий синтаксис в Office 365 PowerShell:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

В этом примере показывается назначение лицензии из `litwareinc:ENTERPRISEPACK` план лицензирования (Office 365 для предприятий E3) нелицензированных пользователю `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Чтобы назначить лицензию большому количеству пользователей, используйте в следующий синтаксис:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Примечания**
  
- Невозможно назначить пользователю несколько лицензий из одного плана лицензирования.
    
- Если у вас нет достаточного количества доступных лицензий, назначаются лицензии для пользователей в том порядке, в случае возвращаемых командлетом **Get-MsolUser** , пока не истечет доступных лицензий.
    
В этом примере показывается назначение лицензии из `litwareinc:ENTERPRISEPACK` план лицензирования (Office 365 для предприятий E3) для всех пользователей без лицензий.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

В этом примере назначаются те же лицензии пользователям без лицензий из отдела продаж в США.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Подробная версия (инструкции с подробными пояснениями)
<a name="LongVersion"> </a>

Как было указано в статье [Просмотр лицензионной и нелицензированных пользователей с Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), существует возможность для пользователей, имеющих допустимые учетные записи пользователей Office 365, но кто не было выдано лицензии Office 365. Это означает, что учетной записи или нет учетной записи, эти пользователи не смогут войти в Office 365. А если не может войти, невозможно использовать какие-либо службы Office 365.
  
В упомянутой выше статье также сказано, что можно вернуть список учетных записей нелицензированных пользователей с помощью команды:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Эта команда возвращает информацию обо всех пользователях, у которых сейчас нет лицензии на Office 365:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

Как вы видите, у нас есть один нелицензированных пользователей: Светлане Коноваловой. Так как мы перейдите о назначении Светлане лицензии Office 365?
  
Во-первых мы собираемся выполните командлет **Get-MsolAccountSku** , описанные в статье [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):
  
```
Get-MsolAccountSku
```

Эта команда возвращает данные, аналогичные приведенным ниже.
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

Почему мы запустить **Get-MsolAccountSku** ? («Конфигурация» в случае, если вам интересно, — сокращение «единицы складского учета.» В нашем случае, — это просто бизнес-произнесите несколько слов для «продукт».) Существует две причины, почему мы выполнили **Get-MsolAccountSku**. Во-первых нужно убедитесь, что у нас есть лицензии для назначения Светлане. Мы у никаких лицензий, которые можно назначить ему? Чтобы определить, что мы вступили в значение свойства **ActiveUnits** (25) и вычитание значения свойства **WarningUnits** (0) и **ConsumedUnits** (24):
  
 `25 - 0 - 24 = 1`
  
Свойство **ActiveUnits** сообщает нам требуемое количество лицензий, мы приобретения и комбинацией **WarningUnits** и **ConsumedUnits** сообщает нам требуемое количество лицензий в настоящий момент используется. Если мы вычесть числа лицензий, уже голосовые для из числа лицензий, которые мы увидим, мы знаем, требуемое количество лицензий, по-прежнему доступны. Как удачи должен использовать ее, у нас есть одна лицензия для рассылки:
  
 `25 - 0 - 24 = 1`
  
Во-вторых, чтобы назначить новую лицензию необходимо знать имя нашей план лицензирования Светлане (то есть, мы должны знать **AccountSkuId** ). В этом случае очень просто: есть только один план лицензирования ( `litwareinc:ENTERPRISEPACK`). Обратите внимание, что может иметь несколько планы лицензирования в организации. В этом случае **Get-MsolAccountSku** вернет два разных **AccountSkuIds**, и вам потребуется выбрать подходящий план лицензирования при назначении лицензии. В данный момент тем не менее, мы будем пользуйтесь простом случае и Предположим, что у нас есть только один план лицензирования.
  
*Затем так как назначить Светлане Коноваловой новую лицензию?* Типа того:
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Это также вам нужно сделать: просто вызовите командлет **Set-MsolUserLicense** , убедившись, что задан параметр _UserPrincipalName_ для пользователя и соответствующего плана лицензирования.
  
**Set-MsolUserLicense** завершении запущена, вы увидите, что-то похожее на этот на экране:
  
 `PS C:\\windows\\system32>`
  
Другими словами он не будет похож на что-либо выполнена. Чтобы убедиться, что пользователю назначена лицензия, выполните команду следующим образом:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

Если все сработало, вы увидите, что для свойства isLicensed Светланы теперь имеет значение True:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! Примечание по безопасности] хороший вопрос: что делать, если ошибки и попытка присвоить лицензии пользователь, который уже имеет лицензии? Приведет к давая две лицензии для одного пользователя? > Быстрый ответ? Нет; Office 365 не позволяет назначить несколько лицензий с одним пользователем. (, Несколько лицензий из того же план лицензирования, который является.) При попытке выполнить, команда завершится с ошибкой с следующее сообщение об ошибке: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> признать, это сообщение об ошибке немного заблуждение: лицензия не будет действительно недопустимый, он просто назначается пользователю пользователей, которые уже *имеет* лицензии. Но, сообщение об ошибке, важно помнить, что один пользователь не получают несколько лицензий.
  
Как вы только что видно, это очень простой в использовании Office 365 PowerShell назначение отдельная лицензия на одного пользователя. И, которая приводит к следующим изменениям очевидны вопрос: было бы просто, может быть еще проще назначить одну лицензию для одного пользователя с помощью центра администрирования Office 365? Ну, может; который зависит от, частично ли вы удобнее с помощью Windows PowerShell или удобнее с помощью центра администрирования Office 365. Где действительно ярко проявляются Windows PowerShell, однако при им необходимо назначить несколько лицензий для нескольких пользователей. Например эта команда назначает лицензии Office 365 для всех пользователей, которые еще не были установлены лицензии:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

В предыдущей команде используются **Такую** и параметр _UnlicensedUsersOnly_ для возврата коллекции всех учетных записей нелицензированных пользователей. Затем мы передаем этой коллекции в командлет **Set-MsolUserLicense** ; в свою очередь, **Set-MsolUserLicense** назначает лицензии (взяты из `litwareinc:ENTERPRISEPACK` план лицензирования) для каждого пользователя в коллекции.
  
AH, но что делать, если у вас есть 5 нелицензированных пользователей, но только один доступные лицензии? В этом случае **Set-MsolUserLicense** предоставит доступные лицензии для первого пользователя, возвращенного **Get-MsolUser**. **Set-MsolUserLicense** принимающий попытается назначить лицензию четыре другим пользователям, но все четыре из этих попыток завершится ошибкой, а также следующее сообщение об ошибке:
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
Другими словами Set-MsolUserLicense не будут давать сбой. Вместо этого он будет назначить любое количество лицензий, его можно. Только после этого он завершится ошибкой.
  
Давайте попробуйте другой пример. Возможно, вам нужно выполнить назначении лицензии для всех пользователей в отделе продаж. Ничего:
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Чтобы выполнить задачу посложнее и свести к минимуму сообщения об ошибках и компьютерную обработку, просто назначьте лицензию нелицензированным пользователям из отдела продаж.
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

В конце концов нет смысла попытке лицензии пользователям, которые уже имеют лицензию. Как мы уже видели, который не будут работать.
  
Еще один пример. Возможно, вам нужно выполнить лицензии все пользователи США, у которых нет в настоящее время лицензии Office 365. В этом случае:
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

И так далее.
  
> [!NOTE]
> Сколько времени для выполнения команды, скажем, выдает лицензии все нелицензированных пользователей? Это трудно сказать: зависит от числа пользователей, необходимо выполнить скорость подключения к сети. Если у вас есть несколько сотен пользователям пройдет достаточно быстро лицензии (то есть, его не следует занять более чем за минуту или две). Если у вас есть 10 000 пользователей, чтобы лицензировать его очевидно, что займет немного больше времени. Но не такая при условии, что потребуется для назначения лицензий на 10 000 пользователей с помощью центра администрирования Office 365. 
  
До тех пор, пока мы по этой теме, здесь — это что-то необходимо уделить особое внимание при назначении лицензии: Если пользователь не имеет значения, настроенные для свойства **UsageLocation** не сможет назначить этому пользователю лицензии Office 365. Вместо этого вы получите сообщение об ошибке следующего вида:
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
Таким образом, несколько roundabout это сообщение об ошибке сообщает нам о том, что пользователь не присвоен **UsageLocation**. Как можно было бы подумать, свойство **UsageLocation** (которая означает региона или страны, где пользователь обычно используется Office 365) очень важно. Почему? Так как службы, доступные пользователю зависит не только от пакета лицензирования, но также приобрести на котором находится пользователь: из-за локальных правил и правилам, некоторые службы могут быть недоступны для некоторых пользователей. Если пользователь не имеет **UsageLocation**, Office 365 не имеет возможности узнать, какие службы юридическую может быть доступно этому пользователю. Таким образом, Office 365 предоставление какие-либо службы для этого пользователя, по крайней мере не пока не были указаны **UsageLocation** .
  
> [!NOTE]
> При настройке учетной записи пользователя вы узнаете сразу же если имеется каких-либо ограничений лицензии, связанные с указанной части мира. Например, если изменить **UsageLocation** для лицензированных пользователей в Иране ( `IR`), команда завершится с ошибкой с данное сообщение об ошибке: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> потому, что Office 365 не доступен для пользователей в Иране. Для получения дополнительных сведений см [об ограничениях лицензии](https://go.microsoft.com/fwlink/p/?LinkId=691730). Заметим страны двухбуквенный код, создаваемый международной организацией по стандартизации (ISO) используются Office 365. Эти коды можно найти на [веб-сайте ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073). 
  
Если вы хотите убедиться, что данный пользователь имеет **UsageLocation** , можно использовать команду, аналогичную этой:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

Кроме того можно вернуть список всех пользователей, у которых нет **UsageLocation** с помощью следующей команды:
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> При назначении лицензии пользователя этого пользователя будет по умолчанию предоставлен доступ ко всем службам Office 365, для которых есть доступ к вашей организации. К примеру Если вы приобрели лицензии для Office 365 для предприятий E3, недавно лицензированных пользователей будет автоматически предоставлен доступ к службам Exchange Online, Скайп для бизнеса в Интернет и SharePoint Online. Если вы хотите ограничить доступ пользователей к этим службам (например, может потребоваться пользователям иметь доступ к SharePoint Online, но *не* в Exchange Online и Скайп для бизнеса в Интернет) выберите в статье [отключить доступ к службам Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md). 
  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>См. также
<a name="SeeAlso"> </a>

Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:
  
- [Создание учетных записей пользователей с помощью PowerShell в Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Блокировка учетных записей пользователей с помощью PowerShell в Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [SET-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [SELECT-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

