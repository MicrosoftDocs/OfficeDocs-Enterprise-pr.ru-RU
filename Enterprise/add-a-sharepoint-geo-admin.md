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
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="d87c8-103">Добавление или удаление администратора geo в OneDrive несколькими-географически Busniess</span><span class="sxs-lookup"><span data-stu-id="d87c8-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="d87c8-p101">Можно настроить отдельные администраторов для каждого географического расположения, у вас есть клиента. Эти администраторы будут иметь доступ к SharePoint Online и OneDrive параметры, относящиеся к их географического расположения.</span><span class="sxs-lookup"><span data-stu-id="d87c8-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="d87c8-p102">Некоторые службы — например, банк терминов - из центрального расположения для администрирования и были реплицированы во вспомогательных расположения. Admin географически для центрального расположения имеет доступ к ним, а не "Администраторы" географического расположения вспомогательных.</span><span class="sxs-lookup"><span data-stu-id="d87c8-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="d87c8-108">Для получения доступа к параметрам в все географического расположения продолжить глобальных администраторов и администраторов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d87c8-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="d87c8-109">Настройка географически администраторов</span><span class="sxs-lookup"><span data-stu-id="d87c8-109">Configuring geo administrators</span></span>

<span data-ttu-id="d87c8-110">Географическая "Администраторы" для настройки требуется модуль SharePoint Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d87c8-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="d87c8-111">Используйте [Connect-sposervice открывает](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) для подключения к центру администрирования географически расположение, где требуется добавить администратора географически. (Например, Connect-sposervice открываетhttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="d87c8-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="d87c8-112">Для добавления пользователя в качестве администратора географически, выполните`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="d87c8-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="d87c8-113">Чтобы просмотреть существующие Администраторы географического расположения, выполните`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="d87c8-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="d87c8-114">Чтобы удалить пользователя администратором географического расположения, выполните`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="d87c8-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="d87c8-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d87c8-115">See Also</span></span>

[<span data-ttu-id="d87c8-116">Добавление SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="d87c8-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="d87c8-117">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="d87c8-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="d87c8-118">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="d87c8-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)