---
title: Добавление или удаление администратора географически
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Узнайте, как добавить или удалить администратора geo в OneDrive для бизнеса Multi-географически.
ms.openlocfilehash: b88467cf2f33ec3a3a8bf6c2d6927e69e9f7af65
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Добавление или удаление администратора geo в OneDrive несколькими-географически Busniess

Можно настроить отдельные администраторов для каждого географического расположения, у вас есть клиента. Эти администраторы будут иметь доступ к SharePoint Online и OneDrive параметры, относящиеся к их географического расположения.

Некоторые службы — например, банк терминов - из центрального расположения для администрирования и были реплицированы во вспомогательных расположения. Admin географически для центрального расположения имеет доступ к ним, а не "Администраторы" географического расположения вспомогательных.

Для получения доступа к параметрам в все географического расположения продолжить глобальных администраторов и администраторов SharePoint Online.

## <a name="configuring-geo-administrators"></a>Настройка географически администраторов

Географическая "Администраторы" для настройки требуется модуль SharePoint Online PowerShell.

Используйте [Connect-sposervice открывает](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) для подключения к центру администрирования географически расположение, где требуется добавить администратора географически. (Например, Connect-sposervice открываетhttps://ContosoEUR-admin.sharepoint.com.)

Чтобы просмотреть существующие Администраторы географического расположения, выполните`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Добавление пользователя в качестве администратора географически

Для добавления пользователя в качестве администратора географически, выполните`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Чтобы удалить пользователя администратором географического расположения, выполните`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Добавление группы в качестве администратора географически

Можно добавить группу безопасности или группу безопасности с включенной поддержкой почты как администратор географически. (Группы рассылки и группы Office 365 не поддерживаются).

Чтобы добавить группу географически администратором, выполните`Add-SPOGeoAdministrator -GroupAlias <alias>`

Чтобы удалить группу как географически администрирования, выполните`Remove-SPOGeoAdministrator -GroupAlias <alias>`

Обратите внимание, что не все группы безопасности псевдоним группы. Если вы хотите добавить группу безопасности, для которого не псевдоним, запустите [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) для получения списка групп, найдите группу безопасности ObjectID и выполните:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Чтобы удалить группу с помощью ObjectID, выполните`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a>Доступ к центру администрирования для конкретного географического расположения

Для администрирования параметров OneDrive для их географического расположения, "Администраторы" необходимо получить доступ к центру администрирования OneDrive напрямую с помощью следующий формат URL-адреса:

https://admin.onedrive.com/?geo=<*географическая*>

К примеру, Центр администрирования OneDrive для Канады расположена в каталоге: https://admin.onedrive.com/?geo=CAN.

## <a name="see-also"></a>См. также

[Добавление SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Настройка псевдонима (MailNickName) для группы безопасности](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)