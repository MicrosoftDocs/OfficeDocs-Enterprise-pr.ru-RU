---
title: Добавление или удаление администратора географически
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Узнайте, как добавить или удалить администратора geo в OneDrive для бизнеса Multi-географически.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Добавление или удаление администратора geo в OneDrive несколькими-географически Busniess

Можно настроить отдельные администраторов для каждого географического расположения, у вас есть клиента. Эти администраторы будут иметь доступ к SharePoint Online и OneDrive параметры, относящиеся к их географического расположения.

Некоторые службы — например, банк терминов - из центрального расположения для администрирования и были реплицированы во вспомогательных расположения. Admin географически для центрального расположения имеет доступ к ним, а не "Администраторы" географического расположения вспомогательных.

Для получения доступа к параметрам в все географического расположения продолжить глобальных администраторов и администраторов SharePoint Online.

## <a name="configuring-geo-administrators"></a>Настройка географически администраторов

Географическая "Администраторы" для настройки требуется модуль SharePoint Online PowerShell.

Используйте [Connect-sposervice открывает](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) для подключения к центру администрирования географически расположение, где требуется добавить администратора географически. (Например, Connect-sposervice открываетhttps://ContosoEUR-admin.sharepoint.com.)

Для добавления пользователя в качестве администратора географически, выполните`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Чтобы просмотреть существующие Администраторы географического расположения, выполните`Get-SPOGeoAdministrators`

Чтобы удалить пользователя администратором географического расположения, выполните`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="see-also"></a>См. также

[Добавление SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)