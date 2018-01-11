---
title: "Просмотр лицензий и служб с помощью PowerShell в Office 365"
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
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: "Объясняет, как использовать Office 365 PowerShell для просмотра сведений о лицензировании планы, служб и лицензий, которые доступны в организации Office 365."
ms.openlocfilehash: f43a1c20be157d26ec9cd1d98df2f5e17517b1d6
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Просмотр лицензий и служб с помощью PowerShell в Office 365

**Сводка:** Объясняет, как использовать Office 365 PowerShell для просмотра сведений о лицензировании планы, служб и лицензий, которые доступны в организации Office 365.
  
Каждой подписки Office 365 состоит из следующих элементов:
- **Планы лицензирования** Они также известны планы aslicense или планов Office 365. Планы лицензирования определяют службы Office 365, которые будут доступны пользователям. Подписки Office 365 может содержать несколько планы лицензирования. Пример плана лицензирования будет Microsoft Office 365 для предприятий E3.
    
- **Службы** Это также известные asservice планов. Службы, продуктов Office 365, функций и возможностей, доступных в каждом плане лицензирования, например Exchange Online и Office профессиональный плюс. Пользователи могут иметь несколько лицензий, назначенные им из разных планы лицензирования, предоставление доступа для различных служб.
    
- **Лицензии** Каждый план лицензирования содержит число лицензий, приобретенных. Назначение лицензий пользователям, поэтому они могут использовать службы Office 365, которые определены в плане лицензирования. Каждой учетной записи пользователя требуется по крайней мере один лицензии из одного плана лицензирования, выполните вход в Office 365 и с помощью служб.
    
Office 365 PowerShell можно использовать для просмотра сведений о доступные планы лицензирования, лицензии и службы в организации Office 365. Дополнительные сведения о продуктах, компонентов и служб, доступных в различных подписок на Office 365 можно [Параметры плана Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).
## <a name="before-you-begin"></a>Перед началом работы
<a name="RTT"> </a>

- Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Сценарий PowerShell, который автоматизирует процедур, описанных в этом разделе. В частности сценарий позволяет просматривать и отключения службы в организации Office 365, включая Sway. Дополнительные сведения можно [отключить доступ к Sway с Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>Просмотр сведений о планах лицензирования и доступных лицензиях
<a name="ShortVersion"> </a>

Чтобы просмотреть сводную информацию о текущем планы лицензирования и доступных лицензий для каждого плана, выполните следующую команду в Office 365 PowerShell:
  
```
Get-MsolAccountSku
```

Результаты содержат сведения, указанные ниже.
  
- **AccountSkuId:** Показать доступные планы лицензирования для вашей организации, используя синтаксис `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ — это значение, что и при участвуют в Office 365 и является уникальным для вашей организации. _<LicensingPlan>_ Равны для всех пользователей. Например, в значении `litwareinc:ENTERPRISEPACK`, — это название компании `litwareinc`и имя плана лицензирования `ENTERPRISEPACK`, — имя системы для Office 365 для предприятий E3.
    
- **ActiveUnits:** Число лицензий, что покупки для конкретного плана лицензирования.
    
- **WarningUnits:** Число лицензий в плане лицензирования, который еще не обновленной и, срок действия 30-дневный льготный период.
    
- **ConsumedUnits:** Число лицензий, которые вы назначили для пользователей с определенным плана лицензирования.
    
Чтобы просмотреть подробные сведения о службах Office 365, которые доступны во всех планов лицензии, выполните следующую команду:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

В следующей таблице показаны планов обслуживания Office 365 и их понятные имена для наиболее распространенных служб. Список планов обслуживания может отличаться. Полный список планов обслуживания и их понятные имена обратитесь в службу [Поддержки Microsoft Office](https://support.office.com/home/contact).
  
|Служба плана ***|Описание ***|
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
   
Чтобы просмотреть подробные сведения о службах Office 365, доступными в определенных плана лицензирования, используйте следующий синтаксис.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

В этом примере показано служб Office 365, доступные в плане лицензирования litwareinc: enterprisepack (Office 365 для предприятий E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>Никогда не работали с Office 365?
<a name="ShortVersion"> </a>

||
|:-----|
|![Короткие значок обучения LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Создать в Office 365?**         Обнаружение Бесплатные курсы видео для [ИТ-специалистов и администраторов Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), с LinkedIn обучения. |
   
## <a name="see-also"></a>См. также
<a name="ShortVersion"> </a>

#### 

[Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) .
  
[Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md) .
#### 

[Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

