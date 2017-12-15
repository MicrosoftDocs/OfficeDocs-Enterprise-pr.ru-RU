---
title: "Отключение доступа к службам во время назначения лицензий"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "Сведения о том, как назначать лицензии для учетных записей пользователей и отключать определенные планы обслуживания, используя PowerShell в Office 365."
ms.openlocfilehash: 907314e13b353e5d5ddbcd8fe467db568473d0b3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>Отключение доступа к службам во время назначения лицензий

**Сводка:**  Узнайте, как назначение лицензий для учетных записей пользователей и отключение планов обслуживания, определенных в то же время, с помощью Office 365 PowerShell.
  
Подписки на Office 365 включают в себя планы обслуживания для отдельных служб. Администраторам Office 365 часто нужно отключать определенные планы при назначении лицензий для пользователей. Следуя инструкциям в этой статье, вы можете с помощью PowerShell назначить лицензию на Office 365 для одной или нескольких учетных записей пользователей, при этом отключив определенные планы обслуживания.
  
> [!NOTE]
> В основе этой статьи лежит работа Siddhartha Parmar, специалиста технической поддержки Майкрософт, занимающегося эскалированными запросами на обслуживание. 
  
## <a name="before-you-begin"></a>Приступая к работе

Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>Соберите сведения о подписках и планах обслуживания

Выполните эту команду, чтобы увидеть текущие подписки:
  
```
Get-MsolAccountSku
```

Значение составляющих команды  `Get-MsolAccountSku`:
  
- **Включает параметры AccountSkuId** является подписки для вашей организации в \<OrganizationName >:\<подписки > формат. \<OrganizationName > — это значение, что и при участвуют в Office 365 и является уникальным для вашей организации. \<Подписки > значение предназначено для конкретной подписки. Например для litwareinc: enterprisepack, litwareinc — это название организации и ENTERPRISEPACK (Office 365 для предприятий E3) — это имя подписки.
    
- **ActiveUnits**  количество лицензий, которые вы приобрели для подписки.
    
- **WarningUnits**  количество лицензий для не продленной подписки, срок действия которой истекает через 30 дней льготного периода.
    
- **ConsumedUnits**  количество лицензий, которые вы назначили пользователям для подписки.
    
Укажите AccountSkuId для подписки на Office 365, где обозначены пользователи, которым вы хотите назначить лицензию. Убедитесь, что лицензий для назначения достаточно (отнимите **ConsumedUnits** от **ActiveUnits** ).
  
Затем выполните эту команду, чтобы просмотреть сведения о планах обслуживания Office 365, доступных для каждой из ваших подписок:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Просмотрите результаты команды и определите, какие планы обслуживания нужно отключить при назначении лицензий пользователям.
  
Ниже приведен неполный список планов обслуживания и соответствующих им служб Office 365.
  
|**План обслуживания**|**Описание**|
|:-----|:-----|
|SWAY  <br/> |Sway  <br/> |
|INTUNE_O365  <br/> |Управление мобильными устройствами для Office 365  <br/> |
|YAMMER_ENTERPRISE  <br/> |Yammer  <br/> |
|RMS_S_ENTERPRISE  <br/> |Azure Rights Management (RMS)  <br/> |
|OFFICESUBSCRIPTION  <br/> |Office профессиональный плюс  <br/> |
|MCOSTANDARD  <br/> |Skype для бизнеса Online  <br/> |
|SHAREPOINTWAC  <br/> |Office Online  <br/> |
|SHAREPOINTENTERPRISE  <br/> |SharePoint Online  <br/> |
|EXCHANGE_S_ENTERPRISE  <br/> |Exchange Online (план 2)  <br/> |
   
Теперь, когда у вас есть AccountSkuId и планы обслуживания, которые нужно отключить, вы можете назначить лицензии для одного или нескольких пользователей.
  
## <a name="for-a-single-user"></a>Для одного пользователя

Для одного пользователя, заполните поля в имя участника-пользователя учетной записи пользователя, AccountSkuId и список планов обслуживания для отключения и удаления пояснительным текстом и \< и > символов. Выполните результирующий команды в командной строке PowerShell.
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

Ниже приведен пример блока команд для учетной записи belindan@contoso.com. В этом случае указана лицензия contoso:ENTERPRISEPACK, а отключить нужно планы обслуживания RMS_S_ENTERPRISE, SWAY, INTUNE_O365 и YAMMER_ENTERPRISE.
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a>Для нескольких пользователей

Чтобы выполнить эту задачу администрирования для нескольких пользователей, создайте текстовый файл с разделителями-запятыми (CSV-файл), содержащий поля UserPrincipalName и UsageLocation. Пример:
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

После этого укажите расположение входного и выходного CSV-файлов, ИД SKU учетной записи и список планов обслуживания, которые нужно отключить. Затем выполните полученные команды в командной строке PowerShell.
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Что делает этот блок команд PowerShell:
  
- Отображает имя участника-пользователя для каждого пользователя.
    
- Назначает настраиваемые лицензии для каждого пользователя.
    
- Создает CSV-файл со всеми обработанными пользователями и отображает состояние их лицензий.
    
## <a name="see-also"></a>See also

#### 

[Отключение доступа к службам с помощью Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)
  
[Отключение доступа к Sway с помощью PowerShell в Office 365](disable-access-to-sway-with-office-365-powershell.md)
  
[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)

