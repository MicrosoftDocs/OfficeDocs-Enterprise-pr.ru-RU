---
title: "Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей"
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
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям."
ms.openlocfilehash: d419aab9b3287364567e03accdfb2e687eacb0de
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей

**Сводка:** Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям.
  
## <a name="before-you-begin"></a>Приступая к работе

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Чтобы просмотреть сведения о лицензировании плана ( **AccountSkuID** ) в организации, в следующих разделах:
    
  - [Просмотр лицензий и служб с помощью PowerShell в Office 365](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md)
    
- Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.
    
## <a name="the-short-version-instructions-without-explanations"></a>Краткая версия (инструкции без пояснений)
<a name="ShortVersion"> </a>

В этом разделе процедуры представлены без лишних слов и объяснений. Если у вас возникнут вопросы или вам потребуются дополнительные сведения, вы можете прочитать остальные разделы статьи.
  
Чтобы удалить лицензии из учетной записи пользователя, используйте следующий синтаксис:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) с BelindaN@litwareinc.com учетной записи пользователя.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Чтобы удалить лицензии из группы лицензированных пользователей, используйте один из следующих способов:
  
- **Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) от всех accounts для сотрудников отдела продаж в США.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Использование списка определенных учетных записей** Для этого выполните следующие действия:
    
1. Создайте и сохраните текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Используйте следующий синтаксис:
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) из учетных записей пользователей, определенных в текстовый файл C:\My Documents\Accounts.txt.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Чтобы удалить лицензии из всех учетных записей пользователей, используйте следующий синтаксис:
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензий (Office 365 для предприятий E3) для всех существующих учетных записей пользователей с корпоративным лицензированием.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Подробная версия (инструкции с подробными пояснениями)
<a name="LongVersion"> </a>

Ничего не продолжается на непрерывно и, которая включает в себя лицензий на Office 365: быстрее или более поздних версий, поступит время, когда следует удалить лицензии из учетной записи пользователя. Возможно, вам будет пользователя на выходе; Возможно, вам больше не требуются лицензии; может быть -, существует очевидно, что любое количество причин, почему может потребоваться удаление пользовательской лицензии.
  
Прежде чем продолжать любые дополнительные важно Обратите внимание на то, что удаление лицензия требуется для также, удалить лицензии: отключение всех служб на лицензия не то же самое удаление лицензии. Например предположим, что мы использовали копирование наших лицензии Office 365; Другими словами, мы имеет нет доступных никакой лицензии. Вы решили выполните процедуру в разделе [запрещать доступ к службам с помощью Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) , чтобы отключить все службы, скажем, Светлане Коноваловой для учетной записи. После этом, что количество лицензий будет у нас есть доступных? Верно: нулю. Да, процедуры из этого раздела будет *Отключить* всех служб на лицензия, но он не будет отключен (то есть, удаление) сама лицензия. Лицензии все еще будут действовать, и он будет по-прежнему будет назначенную. Она просто не сможет эта лицензия для получения доступа к какие-либо службы Office 365.
  
И это важно: Если вы хотите удалить лицензии у пользователя должно фактически *Удалить* лицензии. Отключение всех служб будет мешают пользователю подключиться Office 365, но он не будет Освободите место на свой лицензии. Если вы хотите получить обратно лицензию, назначенную пользователю, вам нужно выполнить команду, подставив свои значения, команда, которая использует параметр _RemoveLicenses_ для непосредственного удаления лицензии, ранее назначенную Светлане:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Выполнения этой команды и Светлане Коноваловой больше не будет лицензии на использование Office 365.
  
> [!NOTE]
> Как вы видите, если используется параметр _RemoveLicenses_ , необходимо указать имя лицензии, который требуется удалить. Если вы не знаете, какой план лицензирования использовалась при назначении лицензии пользователя, просто выполните команду следующего вида:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
Чтобы убедиться, что лицензия удалена, выполните такую команду, чтобы проверить интересующую учетную запись пользователя:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

Если все выполнено согласно плану, для свойства **isLicensed** Светланы теперь должно быть задано `False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

Другой способ освободить лицензия — путем удаления учетной записи пользователя. Для получения дополнительных сведений см [удаления и восстановления учетных записей пользователей с Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>См. также

Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:
  
- [Создание учетных записей пользователей с помощью PowerShell в Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Блокировка учетных записей пользователей с помощью PowerShell в Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [SET-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

||
|:-----|
|![Короткие значок обучения LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Создать в Office 365?**         Обнаружение Бесплатные курсы видео для [ИТ-специалистов и администраторов Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), с LinkedIn обучения. |
   

