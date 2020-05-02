---
title: Отключение доступа к службам во время назначения лицензий
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Сведения о том, как назначать лицензии для учетных записей пользователей и отключать определенные планы обслуживания, используя PowerShell в Office 365.
ms.openlocfilehash: a00a1af02aeb69f7d69f9f9fc998202ac7c53291
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004672"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>Отключение доступа к службам во время назначения лицензий

Подписки на Office 365 включают в себя планы обслуживания для отдельных служб. Администраторам Office 365 часто нужно отключать определенные планы при назначении лицензий для пользователей. Следуя инструкциям в этой статье, вы можете с помощью PowerShell назначить лицензию на Office 365 для одной или нескольких учетных записей пользователей, при этом отключив определенные планы обслуживания.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Затем перечислите план лицензирования для клиента с помощью этой команды.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Затем получите имя для входа учетной записи, к которой требуется добавить лицензию, также называемую именем участника-пользователя (UPN).

Затем скомпилируйте список служб, которые нужно включить. Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

В приведенном ниже блоке команд введите имя участника пользователя для учетной записи пользователя, номер детали SKU и список планов обслуживания, чтобы включить и удалить пояснительный текст, а также \< символы и >. Затем выполните полученные команды в командной строке PowerShell.
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Затем выполните следующую команду, чтобы просмотреть текущие подписки:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени. Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>

Значение составляющих команды  `Get-MsolAccountSku`:
  
- **AccountSkuId** — это подписка вашей организации в формате \<НазваниеОрганизации>:\<Подписка>. \<НазваниеОрганизации> — значение, которое вы указали при регистрации в Office 365 (уникальное для организации). \<Подписка> — значение, обозначающее конкретную подписку. Например, в случае litwareinc:ENTERPRISEPACK название организации — litwareinc, а название подписки — ENTERPRISEPACK (Office 365 корпоративный E3).
    
- **ActiveUnits**  количество лицензий, которые вы приобрели для подписки.
    
- **WarningUnits** — количество лицензий для не продленной подписки, срок действия которой истекает через 30 дней льготного периода.
    
- **ConsumedUnits**  количество лицензий, которые вы назначили пользователям для подписки.
    
Укажите AccountSkuId для подписки на Office 365, где обозначены пользователи, которым вы хотите назначить лицензию. Убедитесь, что лицензий для назначения достаточно (отнимите **ConsumedUnits** от **ActiveUnits** ).
  
Затем выполните эту команду, чтобы просмотреть сведения о планах обслуживания Office 365, доступных для каждой из ваших подписок:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Просмотрите результаты команды и определите, какие планы обслуживания нужно отключить при назначении лицензий пользователям.
  
Ниже приведен неполный список планов обслуживания и соответствующих им служб Office 365.

В следующей таблице показаны планы обслуживания Office 365 и их понятные имена для наиболее распространенных служб. Ваш список планов обслуживания может отличаться. 
  
|**План обслуживания**|**Описание**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office 365 профессиональный плюс  <br/> |
| `MCOSTANDARD` <br/> |Skype для бизнеса Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (план 2)  <br/> |
   
Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).
   
Теперь, когда у вас есть AccountSkuId и планы обслуживания, которые нужно отключить, вы можете назначить лицензии для одного или нескольких пользователей.
  
### <a name="for-a-single-user"></a>Для одного пользователя

Введите имя участника-пользователя из учетной записи пользователя, AccountSkuId и список отключаемых планов обслуживания, удалив при этом пояснительный текст и символы \< и >. После этого выполните полученные команды в командной строке PowerShell.
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

Ниже приведен пример блока команд для учетной записи belindan@contoso.com. В этом случае указана лицензия contoso:ENTERPRISEPACK, а отключить нужно планы обслуживания RMS_S_ENTERPRISE, SWAY, INTUNE_O365 и YAMMER_ENTERPRISE.
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>Для нескольких пользователей

Чтобы выполнить эту задачу администрирования для нескольких пользователей, создайте текстовый файл с разделителями-запятыми (CSV-файл), содержащий поля UserPrincipalName и UsageLocation. Пример:
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

После этого укажите расположение входного и выходного CSV-файлов, ИД SKU учетной записи и список планов обслуживания, которые нужно отключить. Затем выполните полученные команды в командной строке PowerShell.
  
```powershell
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Что делает этот блок команд PowerShell:
  
- Отображает имя участника-пользователя для каждого пользователя.
    
- Назначает настраиваемые лицензии для каждого пользователя.
    
- Создает CSV-файл со всеми обработанными пользователями и отображает состояние их лицензий.
    
## <a name="see-also"></a>См. также

[Отключение доступа к службам с помощью Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)
  
[Отключение доступа к Sway с помощью PowerShell в Office 365](disable-access-to-sway-with-office-365-powershell.md)
  
[Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
