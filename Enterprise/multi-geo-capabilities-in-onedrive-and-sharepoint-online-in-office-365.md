---
title: Поддержка нескольких регионов в OneDrive и SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Расширьте свою географию присутствия Office 365 с поддержкой нескольких регионов в OneDrive Online.
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948590"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Поддержка нескольких регионов в OneDrive и SharePoint Online

Поддержка нескольких регионов в OneDrive и SharePoint Online обеспечивает управление страной или регионом, в котором хранятся общие ресурсы, такие как сайты групп SharePoint и почтовые ящики групп Office 365.

У каждого пользователя, почтового ящика группы и сайта SharePoint есть предпочтительное расположение данных (PDL), обозначающее географическое расположение для хранения соответствующих данных. Персональные данные пользователей (почтовый ящик Exchange и OneDrive), а также любые созданные им группы Office 365 или сайты SharePoint могут храниться в указанном географическом расположении для соблюдения требований к месту расположения данных. Можно [указывать разных администраторов для каждого географического расположения](add-a-sharepoint-geo-admin.md).

Для пользователей обеспечивается удобство взаимодействия при использовании служб Office 365, включая приложения Office, OneDrive и поиск. Подробные сведения см. в статье [Взаимодействие с пользователем в среде с поддержкой нескольких регионов](multi-geo-user-experience.md).

## <a name="onedrive"></a>OneDrive

Хранилище OneDrive каждого пользователя может быть подготовлено или [перемещено администратором](move-onedrive-between-geo-locations.md) в периферийное расположение в соответствии с предпочтительным расположением данных (PDL) пользователя. После этого личные файлы хранятся в этом географическом расположении, но ими можно делиться с пользователями из других географических расположений.

## <a name="sites-and-groups"></a>Сайты и группы

Когда пользователь создает сайт SharePoint, подключенный к группе, его значение PDL используется для определения географического расположения, в котором создается сайт и почтовый ящик связанной группы. (Если значение PDL пользователя не задано или присвоено географическое расположение, не настроенное в качестве периферийного расположения, сайт и почтовый ящик создаются в центральном расположении.)

В службах Office 365, кроме Exchange, OneDrive и SharePoint, отсутствует поддержка нескольких регионов. Однако группы Office 365, созданные с помощью этих служб, помечаются значением PDL создавшего их пользователя, а почтовый ящик Exchange группы и сайт группы SharePoint Office 365 подготавливаются в соответствующем географическом расположении. 

## <a name="managing-the-multi-geo-environment"></a>Управление средой с поддержкой нескольких регионов

Настройка и управление средой с поддержкой нескольких регионов осуществляется через Центр администрирования SharePoint. 

![Снимок экрана: страница географических расположений в Центре администрирования SharePoint](media/sharepoint-multi-geo-admin-center.png)

(Некоторые действия, например перемещение сайта SharePoint или сайта OneDrive, требуют использования Microsoft PowerShell.)

## <a name="see-also"></a>См. также

[Aka.ms/GetMultiGeo ](https://Aka.ms/GetMultiGeo)

[Администрирование среды с поддержкой нескольких регионов](administering-a-multi-geo-environment.md)

[Квоты хранилища SharePoint в средах с поддержкой нескольких регионов](sharepoint-multi-geo-storage-quota.md)

[Администрирование почтовых ящиков Exchange Online в среде с поддержкой нескольких регионов](administering-exchange-online-multi-geo.md)
