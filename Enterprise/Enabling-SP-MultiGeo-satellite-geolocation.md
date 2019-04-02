---
title: 'Включение SharePoint c поддержкой нескольких регионов в периферийном расположении '
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Включение SharePoint c поддержкой нескольких регионов в периферийном расположении.
ms.openlocfilehash: 98666f76a5b3ec055a6f26d30f502c3cc6b6d3bb
ms.sourcegitcommit: 0ddd9b0c9c23dc6479dce9f5701b69d533d76127
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2019
ms.locfileid: "31025202"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>Включение SharePoint c поддержкой нескольких регионов в периферийном расположении 

Эта статья предназначена для глобальных администраторов и администраторов SharePoint, создавших периферийное расположение с поддержкой нескольких регионов **до** того, как возможности поддержки нескольких регионов в SharePoint стали общедоступными 27 марта 2019 г., и не включивших SharePoint с поддержкой нескольких регионов в своих периферийных расположениях. 

>[!Note]
>Если новое географическое расположение добавлено **после 27 марта**, вам не потребуется выполнять эти инструкции, так как в новом географическом расположении уже включены функции поддержки нескольких регионов для OneDrive и SharePoint.

Эти инструкции позволят включить SharePoint в периферийном расположении, чтобы ваши пользователи из периферийных расположений могли использовать возможности OneDrive и SharePoint по поддержке нескольких регионов в Office 365. 

>[!IMPORTANT]
>Обратите внимание, что это одностороннее включение. После настройки режима SPO вы не сможете вернуть свой клиент в режим с поддержкой нескольких регионов только для OneDrive без эскалации запроса в службе поддержки. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>Установка режима SPO для географического расположения

Чтобы установить режим SPO для географического расположения, подключитесь к географическому расположению, для которого нужно задать режим SPO:

1.  Откройте командную консоль SharePoint Online 
2.  Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -учетные данные $credential
3.  Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)
4.  Обычно эта операция занимает около часа, пока выполняются различные резервирования публикаций в службе, а также повторное присвоение метки клиенту. Минимум через 1 час выполните команду Get-SPOMultiGeoExperience.  В результате будет показано, находится ли это географическое расположение в режиме SPO.</br></br>
![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>Некоторые кэши в службе обновляются каждые 24 часа, поэтому возможно, что в течение 24 часов периферийное расположение может периодически работать, как будто оно по-прежнему находится в режиме ODB. Это не приводит к техническим проблемам. 
 
Дополнительные сведения о SharePoint с поддержкой нескольких регионов см. на странице [aka.ms/sharepointmultigeo](https://docs.microsoft.com/ru-RU/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)


