---
title: Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Объясняет, как использовать Office 365 PowerShell для определения служб Office 365, которые были назначены пользователям.
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365

**Сводка:** Объясняет, как использовать Office 365 PowerShell для определения служб Office 365, которые были назначены пользователям.
  
В Office 365, лицензируемые из планы лицензирования (также называемое номера SKU или Office 365 планы) предоставить пользователям доступ к службам Office 365, определенных для этих планов. Тем не менее пользователь может отсутствовать доступ ко всем службам, которые доступны в лицензию, назначенных им. Office 365 PowerShell можно использовать для просмотра состояния службы на учетные записи пользователей. 

## <a name="before-you-begin"></a>Перед началом работы
<a name="RTT"> </a>

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Используйте команды `Get-MsolAccountSku` и `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` для поиска со следующими сведениями:
    
  - Планы лицензирования, доступные в организации.
    
  - Службы, доступные в каждом плане лицензирования, и порядок, в котором они располагаются (индекс).
    
     Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Используйте команду `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` поиск лицензий, назначенных пользователю, и порядок, в котором они являются из списка (индекс).
    
- Если использовать командлет **Get-MsolUser** без параметра _All_, возвращаются только первые 500 учетных записей.
    
<a name="ShortVersion"> </a>
## <a name="the-short-version-instructions-without-explanations"></a>Краткая версия (инструкции без пояснений)

Для просмотра всех служб Office 365 PowerShell, которые пользователь имеет доступ к, используйте следующий синтаксис:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

В этом примере показано служб, с которыми пользователь BelindaN@litwareinc.com имеет доступ. Это показывает службы, которые связаны с всех лицензий, которые были им назначены своей учетной записи.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Этот код показывает службы, к которым у пользователя BelindaN@litwareinc.com есть доступ по первой назначенной ей лицензии (индекс 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Чтобы найти всех лицензированных пользователей, для которых включены или отключены определенные службы, используйте следующий синтаксис:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

В этих примерах используются следующие сведения:
  
- Лицензии, который предоставляет доступ к службам Office 365, которые мы будем рады — это первый лицензии, назначенной для всех пользователей (номер индекса 0).
    
- Службы Office 365, которые мы будем рады, Скайп для бизнеса в Интернет и Exchange Online. Для лицензий, которые связаны с план лицензирования, Скайп для бизнеса в Интернет — 6-й служба, из списка (номер индекса — 5), и Exchange Online — 9 служба перечисленных (индекс равен 8).
    
В этом примере возвращаются все лицензированных пользователей, которым разрешена Скайп для бизнеса в Интернет и Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

В этом примере возвращаются всех лицензированных пользователей, не включенных в Скайп для бизнеса в Интернет или Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<a name="LongVersion"> </a>
## <a name="the-long-version-instructions-with-detailed-explanations"></a>Подробная версия (инструкции с подробными пояснениями)

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>Поиск служб Office 365 PowerShell, которые пользователь имеет доступ к

Важно очевидно, что вам необходимо знать, какие пользователи выданных лицензий на Office 365 и пользователей, которые еще не. (В статье [Просмотр лицензионной и нелицензированных пользователей с Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) для получения дополнительных сведений). Тем не менее просто создавая лицензии Office 365 не сообщает, что-либо о что этого пользователя можно выполнять с помощью Office 365. Можно использовать пользователь Exchange Online или Скайп для бизнеса в Интернет? Можно этому пользователю доступ к SharePoint Online? Он или она имеет доступ к Office профессиональный плюс? Наличия лицензии означает, что пользователь может получить доступ к этим службам. Тем не менее возможности, доступные пользователю зависят от службы, которые будут включены в его лицензии.
  
Так как же нам определять, который компонентов Office 365 пользователь имеет доступ к? Для этого необходимо выполнить команду, подставив свои значения:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

В этой команде используется командлет **Get-MsolUser** возвращает сведения об учетной записи BelindaN@litwareinc.com. Мы возвращении эти сведения, мы передавать данные учетной записи в командлет **Select-Object** и попросите **Select-Object** «разверните» значение свойства **лицензии** :
  
 `Select-Object -ExpandProperty Licenses`
  
Зачем мы это делаем? Также по умолчанию **лицензий** свойство сообщает нам только имя пакета лицензирования, откуда лицензия:
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

«Разворачивание» свойства **Licenses** предоставляет нам немного больше информации:
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

И затем, развернув свойство **ServiceStatus** мы можем вернуть еще больше информации:
  
|Служба плана ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office профессиональный плюс  <br/> |
| `MCOSTANDARD` <br/> |Skype для бизнеса Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (план 2)  <br/> |
   
> [!NOTE]
> Вы сказать, что это слишком много кода? Также, если вы пугает маленьким запутанность Windows PowerShell, можно запустить эту сжатую версию команды вместо: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
В случае, если вам интересно, мы может «разверните узел» свойства **Licenses** поскольку **лицензий** является свойством: это отдельное свойство, которое можно хранить несколько значений. Когда мы разверните значение свойства, которые мы просто детализировать получите эти дополнительные значения, которые по умолчанию не отображаются на экране.
  
> [!NOTE]
> Так как вы должны знать, что значение является многозначным свойством? Чтобы выяснить это, запустите команду следующего вида: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> командлета **Get-member** , возвращает сведения об объекте. в этом случае сведения о свойстве значений, составляющих объект учетной записи пользователя. Вот что может сказать о свойства **Licenses** **Get-Member** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> при определении свойств что-либо говорится о коллекциях (в этом случае `System.Collections.Generic.List`) то вы знаете, вы имеете дело с многозначным свойством. 
  
Так что же это все значит? Чтобы ответить на этот вопрос, сперва новый взгляд на информацию, возвращенную командлетом **Get-MsolUser** :
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

И давайте также взглянем на таблицу, объясняется, что самом деле представляют эти планы обслуживания со странными именами:
  
|Служба плана ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office профессиональный плюс  <br/> |
| `MCOSTANDARD` <br/> |Skype для бизнеса Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (план 2)  <br/> |
   
Этих?  `MCOSTANDARD` — это просто внутренних программирования имен для Скайп для бизнеса в Интернет, а `OFFICESUSBCRIPTION` — это просто внутренних программирования имя для приложений Office профессиональный плюс. Это не самое интуитивно в мире, но до тех пор, пока в этой таблице держать под рукой не будут иметь множество проблем при работе со службами Office 365.
  
Но подождите: больше. Как мы узнали в статье [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), если задано значение **ProvisioningStatus** `Success` , который означает, что служба полностью включен; Например если `MCOSTANDARD` задано значение `Success` , который означает, что пользователь может получить доступ к Скайп для бизнеса в Интернет. Если задано значение **ProvisioningStatus** `PendingInput` , который означает, что Office 365 все еще обрабатывает запрос службы; Тем не менее пользователь может обычно войдите в систему и доступа к службе во время завершения обработки запроса. ( `YAMMER_ENTERPRISE` всегда отображается как `PendingInput`, но это не важно:, который не остановит пользователя подключение к сети Yammer).
  
> [!IMPORTANT]
> Пользователи могут устанавливать и активировать новую установку Office профессиональный плюс при `OFFICESUBSCRIPTION` в `PendingInput` состояние.
  
И нет необходимости говорить, — это служба задано значение `Disabled` , который означает, что соответствующая служба недоступна для пользователя.
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>Поиск пользователей, имеющих доступ к определенным службам Office 365 PowerShell

В отдельных статьях было показано, как использовать Office 365 PowerShell для отключения доступа пользователей к службам. (Если вы пропустили этой статье, см. [Отключение доступа к службам с помощью Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Которая приводит к следующим изменениям очевидны вопрос: какой вид, чтобы определить, какие *Пользователи* (то есть несколько пользователей) имеют служб включен или отключен?
  
Мы надежде, что кто-то задаст. Чтобы ответить на этот вопрос, давайте рассмотрим таблицы службы, которые мы сначала рассмотрены в статье [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) для нашего доступны только план лицензирования `litwareinc:ENTERPRISEPACK`:
  
|Служба плана ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office профессиональный плюс  <br/> |
| `MCOSTANDARD` <br/> |Skype для бизнеса Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (план 2)  <br/> |
   
Как вы помните, план обслуживания не больше, чем внутреннее имя программирования для продукта; например `OFFICESUBSCRIPTION`, имени одно, — это внутреннее имя программирования в Office профессиональный плюс. Если `OFFICESUBSCRIPTION` отображается как `SUCCESS` на план обслуживания пользователя, затем это означает, что пользователь может получить доступ к Office профессиональный плюс. Если `EXCHANGE_S_ENTERPRISE` указана в качестве `DISABLED` , который означает, что пользователь не может использовать Exchange Online.
  
> [!IMPORTANT]
> Пользователи могут устанавливать и активировать новую установку Office профессиональный плюс при `OFFICESUBSCRIPTION` в `PendingInput` состояние.
  
Необходимо на данном этапе где порядок служб играет важнейшую роль. Windows PowerShell присваивает индекс для каждой записи в списке. Первой записи равно 0, следующей записи — 1 и т. д. В следующей таблице описаны результаты:
  
|Номер индекса ***|Служба плана ***|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
Как вы видите, `SWAY` первой службы в списке, поэтому он получает номер индекса 0.
  
> [!CAUTION]
> Почему 0, а не 1? Это связано с программирования очередь. В языки программирования индексы указано, как далеко элемент является «смещение» от начала массива. Первый элемент *является* начала массива, поэтому его смещение равно 0. Второй элемент является 1 элемент от начала массива, поэтому его смещение равно 1.
  
Давайте попробуйте пример. Предположим, что мы хотели бы список всех лицензированных пользователей, которые не были активированы для Exchange Online. Для этого можно использовать следующую команду:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Конечно это шифрованное нужна маленьким команды, давайте уйти около минуты объяснить, как это работает. Это фактически команда двух частей и первая часть очень просто: мы используем командлет **Get-MsolUser** возвращает коллекцию всех наших пользователей Office 365 (лицензированным и нелицензированных):
  
```
Get-MsolUser
```

Эти сведения затем передается в командлет **Where-Object** . **Where-Object** проходит через все учетные записи пользователей и выполняет поиск этих учетных записей, необходимых для обоих следующим критериям:
  
- Для свойства **isLicensed** равно ( `-eq`) `True` ( `$true`). Который позволяет исключить пользователей без лицензий.
    
- Значение лицензий **[0]. ServiceStatus [8]. ProvisioningStatus** свойство равно ( `-eq`) `Disabled`. В нашем интерпретации важной частью имя громоздкими свойства состоит в следующем.
    
     `ServiceStatus[8]`
    
    `[8]` Представляет номер индекса для Exchange Online. (Мы знаем, обратившись в таблице несколько минут назад). Что делать, если требуется найти всем пользователям, включенным для Скайп для бизнеса в Интернет? Также номер индекса для Скайп для бизнеса в Интернет — 5, мы используем следующий синтаксис:
    
     `ServiceStatus[5]`
    
    И так далее.
    
    Заметим `Licenses[0]` указывает, план лицензирования, который нужно просмотреть. Поскольку домена в нашей тестовой среде имеет только один план лицензирования это не имеет значения намного. Однако предположим, что у нас пользователя, которому назначена лицензии из двух разных планы лицензирования. В этом случае `Licenses[0]` представляет первый план лицензирования и `Licenses[1]` представляет второй план лицензирования.
    
    Чтобы найти лицензии, назначенные пользователю, и порядок, в котором они располагаются, выполните следующую команду:
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

Вы видите, как это работает? Номер индекса для приложений Office профессиональный плюс — 4; Таким образом эта команда возвращает список всех пользователей, которые не были активированы для приложений Office профессиональный плюс:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

А что делать, если мы хотели список пользователей, которые были *включены* в Office профессиональный плюс? Если вы был включен, вашей **ServiceStatus** будет `PendingInput` или `Success`; Другими словами, будет вашей **ServiceStatus** *не* равенства ( `-ne`) `Disabled`. Это означает, что все, нужно сделать — вступили в нашей предыдущей команды и заменить `-eq` оператор для `-ne` оператор:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

Как говорят переходит, что код, вероятно, не будут win много Конкурсы преимущество. И достоверность сказали, код может получить еще больше запутанную. Например предположим, что для просмотра для пользователей, которым разрешена для обеих Скайп для бизнеса в Интернет и Exchange Online:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Но не выполнения слишком много о как вас, который может иметь вид: важно, что с относительно небольшим минимальными усилиями, можно извлечь эти сведения. Не удается получить в эти же сведения, с помощью центра администрирования Office 365? Теоретически, Да, но, в практике, нет. Чтобы получить в эти же сведения, с помощью центра администрирования Office 365 необходимо просмотреть сведения о лицензировании для каждого пользователя, один пользователь за раз и затем вручную отслеживание пользователей, которые включены для *X* и пользователей, которые еще не. Который будет работать, но давайте честно: при наличии более чем 10 или 11 пользователей не понадобятся для этого. Это слишком утомительным и занимать много времени.
  
Конечно, являющийся зачем нам Windows PowerShell: Windows PowerShell позволяет сохранить вы утомительные и длительные задачи, например.
  
Ниже приведен пример команды для просмотра сведений о службе для указанного набора служб, как определено в своих лицензий и ServiceStatus индексов для подписки на Office 365 E5:
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

Эта команда создает CSV-файла, все пользователи, а также их состояние службы для указанного набора служб (группы, Yammer, службы управления правами, OfficePro, Скайп, SharePoint и Exchange).

>[!Note]
>Можно получить список служб в подписке из `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` команды. В выходных данных сначала нумерация индексов службы с 0. Предыдущая команда всего лишь пример. Номера индекса для служб может изменяться со временем.
>

  
<a name="SeeAlso"> </a>
## <a name="see-also"></a>См. также

Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:
  
- [Создание учетных записей пользователей с помощью PowerShell в Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Блокировка учетных записей пользователей с помощью PowerShell в Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [SELECT-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]