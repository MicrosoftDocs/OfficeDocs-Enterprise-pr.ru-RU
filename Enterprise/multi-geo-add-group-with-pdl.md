---
title: Создание группы Microsoft 365 с определенным параметром PDL
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: Узнайте, как создать группу Microsoft 365 с указанным предпочтительным расположением данных в среде с поддержкой нескольких регионов.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1648a9c974e7d25d989156c5a8e2d6818727a3b6
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606835"
---
# <a name="create-a-microsoft-365-group-with-a-specific-pdl"></a>Создание группы Microsoft 365 с определенным параметром PDL

Когда пользователи в среде с поддержкой нескольких регионов создают группу Microsoft 365, предпочитаемое местоположение данных для группы автоматически становится равным указанному для пользователя. Глобальные администраторы, администраторы SharePoint и Exchange могут создавать группы в любом выбранном регионе. 

Если нужно создать группу с определенным PDL, можно использовать Центр администрирования SharePoint или командлет Microsoft PowerShell New-UnifiedGroup для Exchange Online. При этом как почтовый ящик группы, так и сайт SharePoint, связанный с группой, подготавливаются в указанном предпочтительном расположении данных (PDL).

Чтобы создать группу Microsoft 365 с указанным параметром PDL, перейдите в центр администрирования SharePoint в географическом расположении, в котором необходимо создать сайт группы.

Пример:

Если нужно создать сайт группы в Австралии, вы можете перейти на страницу https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Нажмите **+ Создать**.
2. Следуйте инструкциям, чтобы создать сайт группы.

Сайт группы будет подготовлен в географическом расположении, соответствующем Центру администрирования SharePoint, из которого вы отправили запрос на создание сайта. 

Использование Exchange PowerShell 

Подключитесь к Exchange Online PowerShell и передайте параметр *- MailBoxRegion* с кодом региона.

Пример: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Снимок экрана: командлет PowerShell New-UnifiedGroup с синтаксисом](media/multi-geo-new-group-with-pdl-powershell.png)

Обратите внимание, что подготовка сайта группы SharePoint выполняется по запросу. В первый раз сайт будет подготовлен владельцем группы или участником, пытающимся получить к нему доступ.

## <a name="geo-location-codes"></a>Коды регионов

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Связанные статьи

[Подключение к PowerShell Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
