---
title: Просмотр лицензий и служб с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: В этой статье рассказывается, как использовать PowerShell для Office 365 для просмотра сведений о планах лицензирования, службах и лицензиях, доступных в организации Office 365.
ms.openlocfilehash: 9ecaad00d46cf920822419ca1ccdd547ff060fa0
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844140"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Просмотр лицензий и служб с помощью PowerShell в Office 365

Каждая подписка на Office 365 состоит из следующих элементов:

- **Планы лицензирования** Они также называются планами лицензирования или планами Office 365. Планы лицензирования определяют службы Office 365, доступные пользователям. Ваша подписка на Office 365 может содержать несколько планов лицензирования. Примером может служить план лицензирования Office 365 корпоративный E3.
    
- **Службы** Они также называются планами обслуживания. Службы — это продукты, функции и возможности Office 365, доступные в каждом плане лицензирования, например, Exchange Online и Office профессиональный плюс. Пользователям могут быть назначены несколько лицензий из разных планов лицензирования, которые предоставляют доступ к разным службам.
    
- **Licenses (лицензии** ) Каждый план лицензирования содержит количество приобретенных лицензий. Вы назначаете пользователям лицензии, чтобы они могли использовать службы Office 365, определенные планом лицензирования. Каждая учетная запись пользователя должна иметь по крайней мере одну лицензию из одного плана лицензирования, чтобы пользователи могли входить в Office 365 и использовать службы.
    
Вы можете использовать Office 365 PowerShell для просмотра сведений о доступных планах лицензирования, лицензиях и службах в организации Office 365. Дополнительные сведения о продуктах, возможностях и службах, доступных в различных подписках на Office 365, можно найти в статье [варианты плана office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Чтобы просмотреть сводную информацию о текущих планах лицензирования и доступных лицензиях для каждого плана, выполните следующую команду:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Результаты содержат:
  
- **Скупартнумбер:** Показывает доступные планы лицензирования для вашей организации. Например, `ENTERPRISEPACK` это название плана лицензирования для Office 365 корпоративный E3.
    
- **Включено:** Количество лицензий, приобретенных для определенного плана лицензирования.
    
- **ConsumedUnits:** Количество лицензий, назначенных пользователям из определенного плана лицензирования.
    
Чтобы просмотреть сведения о службах Office 365, доступных во всех планах лицензирования, сначала необходимо отобразить список планов лицензирования.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Затем сохраните сведения о планах лицензии в переменной.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Затем отобразите службы в определенном плане лицензирования.

```powershell
$licenses[<index>].ServicePlans
```

\<Индекс> — это целое число, задающее номер строки плана лицензирования из отображения `Get-AzureADSubscribedSku | Select SkuPartNumber` команды минус 1.

Например, если `Get-AzureADSubscribedSku | Select SkuPartNumber` команда имеет следующий вид:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Затем команда отображает службы для плана лицензирования ЕНТЕРПРИСЕПРЕМИУМ следующим образом:

```powershell
$licenses[2].ServicePlans
```

ЕНТЕРПРИСЕПРЕМИУМ — третья строка. Таким образом, значение индекса — (3-1) или 2.

Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Кроме того, вы можете воспользоваться сценарием PowerShell, который автоматизирует выполнение процедур, описанных в этой статье. В частности, скрипт позволяет просматривать и отключать службы в организации Office 365, в том числе Sway. Дополнительные сведения см. в статье [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Чтобы просмотреть сводную информацию о текущих планах лицензирования и доступных лицензиях для каждого плана, выполните следующую команду:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени. Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>

Результаты содержат сведения, указанные ниже.
  
- **AccountSkuId:** Отображение доступных планов лицензирования для Организации с помощью синтаксиса `<CompanyName>:<LicensingPlan>`.  CompanyName>— это значение, которое вы задаете при регистрации в Office 365 и является уникальным для вашей организации. _ \<_ Значение _ \<>лиценсингплан_ одинаково для всех. Например, в значении `litwareinc:ENTERPRISEPACK`название `litwareinc`компании и название `ENTERPRISEPACK`плана лицензирования, которое является системным именем для Office 365 корпоративный E3.
    
- **ActiveUnits:** Количество лицензий, приобретенных для определенного плана лицензирования.
    
- **WarningUnits:** Количество лицензий в плане лицензирования, которые вы еще не обновили, и срок действия которых истекает через 30 дней.
    
- **ConsumedUnits:** Количество лицензий, назначенных пользователям из определенного плана лицензирования.
    
Чтобы просмотреть сведения о службах Office 365, доступных во всех планах лицензирования, выполните следующую команду:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

В следующей таблице показаны планы обслуживания Office 365 и их понятные имена для наиболее распространенных служб. Ваш список планов обслуживания может отличаться. 
  
|**План обслуживания**|**Описание**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office профессиональный плюс  <br/> |
| `MCOSTANDARD` <br/> |Skype для бизнеса Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (план 2)  <br/> |
   
Полный список планов лицензирования (называемых также названиями продуктов), включенных планов обслуживания и соответствующих понятных имен можно узнать в статье [наименования и идентификаторы планов обслуживания для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Чтобы просмотреть сведения о службах Office 365, доступных в определенном плане лицензирования, используйте следующий синтаксис.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

В этом примере показаны службы Office 365, доступные в плане лицензирования litwareinc: ENTERPRISEPACK (Office 365 корпоративный E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Дополнительные ресурсы

[Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
