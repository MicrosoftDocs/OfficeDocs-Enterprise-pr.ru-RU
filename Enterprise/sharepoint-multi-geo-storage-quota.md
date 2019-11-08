---
title: Квоты хранилища SharePoint в средах с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Сведения о квотах хранилища SharePoint в средах с поддержкой нескольких регионов.
ms.openlocfilehash: d4049312a2da64f16d2637ffd37adf98f2282287
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033385"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>Квоты хранилища SharePoint в средах с поддержкой нескольких регионов

По умолчанию все регионы среды с поддержкой нескольких регионов совместно используют доступную квоту хранилища клиента.

С помощью параметра квоты хранилища географического расположения SharePoint можно управлять квотой хранилища для каждого географического расположения. При выделении квоты хранилища для географического расположения она определяет максимальный объем дискового пространства, доступного для этого географического расположения, и вычитается из доступного дискового пространства клиента. Оставшееся доступное дисковое пространство клиента затем делится между настроенными географическими расположениями, для которых не выделены определенные квоты хранилища.

Квота хранилища SharePoint для любого географического расположения может быть выделена администратором SharePoint Online путем подключения к центральному расположению. Администраторы геообъектов для периферийных расположений могут просматривать квоту хранилища, но не могут ее выделять.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>Настройка квоты хранилища для географического расположения

Используйте [модуль Microsoft SharePoint Online](https://www.microsoft.com/download/details.aspx?id=35588 ) и подключитесь к центральному расположению, чтобы выделить квоту хранилища для географического расположения. 

Чтобы выделить квоту хранилища для расположения, выполните следующий командлет:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

Чтобы просмотреть квоту хранилища для текущего географического расположения, выполните следующую команду:

`Get-SPOGeoStorageQuota`

![Снимок экрана: окно PowerShell с командлетом Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

Чтобы просмотреть квоту хранилища для всех географических расположений, выполните следующую команду:

`Get-SPOGeoStorageQuota -AllLocations`

Чтобы удалить квоту хранилища, выделенную для географического расположения, установите параметр `StorageQuota value = 0`:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
