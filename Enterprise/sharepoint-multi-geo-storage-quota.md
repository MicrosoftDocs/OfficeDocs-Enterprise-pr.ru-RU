---
title: Квоты хранилища SharePoint в средах с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Сведения о квотах хранилища SharePoint в средах с поддержкой нескольких регионов.
ms.openlocfilehash: 9c43f21a844507c4de7971d70a110665ddc094ba
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934076"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>Квоты хранилища SharePoint в средах с поддержкой нескольких регионов

По умолчанию все регионы среды с поддержкой нескольких регионов совместно используют доступную квоту хранилища клиента.

С помощью параметра квоты хранилища географического расположения SharePoint можно управлять квотой хранилища для каждого географического расположения. При выделении квоты хранилища для географического расположения она определяет максимальный объем дискового пространства, доступного для этого географического расположения, и вычитается из доступного дискового пространства клиента. Оставшееся доступное дисковое пространство клиента затем делится между настроенными географическими расположениями, для которых не выделены определенные квоты хранилища.

Квота хранилища SharePoint для любого географического расположения может быть выделена администратором SharePoint Online путем подключения к центральному расположению. Администраторы геообъектов для периферийных расположений могут просматривать квоту хранилища, но не могут ее выделять.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>Настройка квоты хранилища для географического расположения

Используйте [модуль Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588 ) и подключитесь к центральному расположению, чтобы выделить квоту хранилища для географического расположения. 

Чтобы выделить квоту хранилища для расположения, выполните следующий командлет:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

Чтобы просмотреть квоту хранилища для текущего географического расположения, выполните следующую команду:

`Get-SPOGeoStorageQuota`

![Снимок экрана: окно PowerShell с командлетом Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

Чтобы просмотреть квоту хранилища для всех географических расположений, выполните следующую команду:

`Get-SPOGeoStorageQuota -AllLocations`

Чтобы удалить квоту хранилища, выделенную для географического расположения, установите параметр `StorageQuota value = 0`:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`