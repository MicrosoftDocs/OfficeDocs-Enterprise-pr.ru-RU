---
title: Ограничение содержимого по геообъекту
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Узнайте, как ограничить сайты SharePoint определенным географическим расположением в среде с поддержкой нескольких регионов.
ms.openlocfilehash: 59301a591e5465bdcda4aa84a18880961c0b615b
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934077"
---
# <a name="restrict-content-to-a-geo-location"></a>Ограничение содержимого по геообъекту

В некоторых случаях можно выбрать принудительное сохранение сайта и его файлового содержимого в географическом расположении, где он был создан, либо запретив перемещение сайта, либо запретив кэширование его файлового содержимого в другое географическое расположение.

Это можно сделать с помощью командлета [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) с параметром **RestrictedToGeo**. По умолчанию этот параметр имеет значение NULL, но вы можете изменить его на одно из следующих значений:

|Ограничение|Описание|
|:----------|:----------|
|NoRestriction|Сайт можно перемещать в другое географическое расположение.|
|BlockMoveOnly|Сайт нельзя перемещать в другое географическое расположение, но его содержимое можно кэшировать в других географических расположениях.|
|BlockFull|Сайт нельзя перемещать в другое географическое расположение, и полное файловое содержимое не кэшируется в других географических расположениях. Заголовок файлов (полученный из содержимого), имя файла и другие свойства файла по-прежнему могут кэшироваться в других географических расположениях.<br>Содержимое, сохраненное на сайте до настройки значения BlockFull, можно продолжать кэшировать в других географических расположениях.|

Используйте указанный ниже синтаксис.

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Пример:

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
