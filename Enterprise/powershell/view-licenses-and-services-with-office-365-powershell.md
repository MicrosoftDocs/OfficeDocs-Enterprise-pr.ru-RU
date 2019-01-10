---
title: Просмотр лицензий и служб с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Объясняет, как использовать Office 365 PowerShell для просмотра сведений о лицензировании планы, служб и лицензий, которые доступны в организации Office 365.
ms.openlocfilehash: 8efc123e2820560b4bd8547f4c99bccae242956f
ms.sourcegitcommit: 96313c3c812bae47819f603af995839f4da034c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "27786155"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Просмотр лицензий и служб с помощью PowerShell в Office 365

**Сводка:** Объясняет, как использовать Office 365 PowerShell для просмотра сведений о лицензировании планы, служб и лицензий, которые доступны в организации Office 365.
  
Каждой подписки Office 365 состоит из следующих элементов:

- **Планы лицензирования** Это также известной как планы лицензии или планов Office 365. Планы лицензирования определяют службы Office 365, которые будут доступны пользователям. Подписки Office 365 может содержать несколько планы лицензирования. Пример плана лицензирования будет Microsoft Office 365 для предприятий E3.
    
- **Службы** Это также известной как планов обслуживания. Службы, продуктов Office 365, функций и возможностей, доступных в каждом плане лицензирования, например Exchange Online и Office профессиональный плюс. Пользователи могут иметь несколько лицензий, назначенные им из разных планы лицензирования, предоставление доступа для различных служб.
    
- **Лицензии** Каждый план лицензирования содержит число лицензий, приобретенных. Назначение лицензий пользователям, поэтому они могут использовать службы Office 365, которые определены в плане лицензирования. Каждой учетной записи пользователя требуется по крайней мере один лицензии из одного плана лицензирования, выполните вход в Office 365 и с помощью служб.
    
Office 365 PowerShell можно использовать для просмотра сведений о доступные планы лицензирования, лицензии и службы в организации Office 365. Дополнительные сведения о продуктах, компонентов и служб, доступных в различных подписок на Office 365 можно [Параметры плана Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Использование модуля PowerShell Azure Active Directory для Graph

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Чтобы просмотреть сводную информацию о текущем планы лицензирования и доступных лицензий для каждого плана, выполните следующую команду:
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Результаты содержат сведения, указанные ниже.
  
- **SkuPartNumber:** Отображает доступные планы лицензирования для вашей организации. Например `ENTERPRISEPACK` — это имя системы для Office 365 для предприятий E3.
    
- **Включено:** Число лицензий, которые вы приобрели для конкретного плана лицензирования.
    
- **ConsumedUnits:** Число лицензий, которые вы назначили для пользователей с определенным плана лицензирования.
    
Чтобы просмотреть подробные сведения о службах Office 365, которые доступны во всех планов лицензии, сначала отобразите список планов лицензии.

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

Затем сохраните информацию о лицензии планы в переменной.

````
$licenses = Get-AzureADSubscribedSku
````

Затем откройте службы в плане лицензий.

````
$licenses[<index>].ServicePlans
````

\<Индекс > — целое число, указывающее количество план лицензирования из отображения `Get-AzureADSubscribedSku | Select SkuPartNumber` команды минус 1.

Например если на отображение `Get-AzureADSubscribedSku | Select SkuPartNumber` команда будет иметь это:

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

Выберите команду, чтобы отобразить служб для план лицензирования ENTERPRISEPREMIUM состоит в следующем.

````
$licenses[2].ServicePlans
````

ENTERPRISEPREMIUM является третьей строки. Таким образом, — это значение индекса (3 - 1), или 2.

Полный список планов лицензии (также известной как названия продуктов), планы включены службы и их соответствующих понятные имена в разделе [продукта имена и идентификаторы плана службы для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Использование модуля Microsoft Azure Active Directory для Windows PowerShell

Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Чтобы просмотреть сводную информацию о текущем планы лицензирования и доступных лицензий для каждого плана, выполните следующую команду:
  
```
Get-MsolAccountSku
```

Результаты содержат сведения, указанные ниже.
  
- **AccountSkuId:** Показать доступные планы лицензирования для вашей организации, используя синтаксис `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ — это значение, что и при участвуют в Office 365 и является уникальным для вашей организации. _<LicensingPlan>_ Равны для всех пользователей. Например, в значении `litwareinc:ENTERPRISEPACK`, — это название компании `litwareinc`и имя плана лицензирования `ENTERPRISEPACK`, — имя системы для Office 365 для предприятий E3.
    
- **ActiveUnits:** Число лицензий, которые вы приобрели для конкретного плана лицензирования.
    
- **WarningUnits:** Число лицензий в плане лицензирования, который еще не обновленной и, срок действия 30-дневный льготный период.
    
- **ConsumedUnits:** Число лицензий, которые вы назначили для пользователей с определенным плана лицензирования.
    
Чтобы просмотреть подробные сведения о службах Office 365, которые доступны во всех планов лицензии, выполните следующую команду:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

В следующей таблице показаны планов обслуживания Office 365 и их понятные имена для наиболее распространенных служб. Список планов обслуживания может отличаться. 
  
|**План обслуживания**|**Описание**|
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
   
Полный список планов лицензии (также известной как названия продуктов), планы включены службы и их соответствующих понятные имена в разделе [продукта имена и идентификаторы плана службы для лицензирования](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Чтобы просмотреть подробные сведения о службах Office 365, доступными в определенных плана лицензирования, используйте следующий синтаксис.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

В этом примере показано служб Office 365, доступные в плане лицензирования litwareinc: enterprisepack (Office 365 для предприятий E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>Никогда не работали с Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>См. также


[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
