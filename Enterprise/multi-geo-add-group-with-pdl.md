---
title: Создание группы Office 365 с определенным предпочтительным расположением данных (PDL)
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Узнайте, как создать группу Office 365 с указанным предпочтительным расположением данных в среде с поддержкой нескольких регионов.
ms.openlocfilehash: a46a34d9fd5be9b3acda5ee3859f4eed08797b7c
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934083"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>Создание группы Office 365 с определенным предпочтительным расположением данных (PDL)

Когда пользователь в среде с поддержкой нескольких регионов создает группу Office 365, предпочтительному расположению данных группы автоматически присваивается значение, соответствующее этому значению пользователя. Если нужно создать группу с определенным PDL, можно использовать командлет Microsoft PowerShell New-UnifiedGroup для Exchange Online. При этом как почтовый ящик группы, так и сайт SharePoint, связанный с группой, подготавливаются в указанном предпочтительном расположении данных (PDL).

Для выполнения этого действия нужно быть глобальным администратором или администратором SharePoint Online.

Чтобы создать группу Office 365 с указанным PDL, подключитесь к Exchange Online PowerShell и передайте параметр *- MailBoxRegion* с кодом региона.

Пример: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Снимок экрана: командлет PowerShell New-UnifiedGroup с синтаксисом](media/multi-geo-new-group-with-pdl-powershell.png)

Обратите внимание, что подготовка сайта группы SharePoint выполняется по запросу. В первый раз сайт будет подготовлен владельцем группы или участником, пытающимся получить к нему доступ.

## <a name="geo-location-codes"></a>Коды регионов

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>См. также

[Подключение к PowerShell Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)