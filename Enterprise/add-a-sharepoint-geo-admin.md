---
title: Добавление и удаление администратора геообъектов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Узнайте, как добавить или удалить администратора geo в OneDrive для бизнеса Multi-географически.
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849815"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="01487-103">Добавление или удаление администратора geo в OneDrive несколькими-географически Busniess</span><span class="sxs-lookup"><span data-stu-id="01487-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="01487-p101">Можно настроить отдельные администраторов для каждого географического расположения, у вас есть клиента. Эти администраторы будут иметь доступ к SharePoint Online и OneDrive параметры, относящиеся к их географического расположения.</span><span class="sxs-lookup"><span data-stu-id="01487-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="01487-p102">Некоторые службы — например, банк терминов - из центрального расположения для администрирования и были реплицированы во вспомогательных расположения. Admin географически для центрального расположения имеет доступ к ним, а не "Администраторы" географического расположения вспомогательных.</span><span class="sxs-lookup"><span data-stu-id="01487-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="01487-108">Чтобы иметь доступ к параметрам в центрального расположения и все вспомогательные расположения продолжить глобальных администраторов и администраторов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="01487-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="01487-109">Настройка географически администраторов</span><span class="sxs-lookup"><span data-stu-id="01487-109">Configuring geo administrators</span></span>

<span data-ttu-id="01487-110">Географическая "Администраторы" для настройки требуется модуль SharePoint Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01487-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="01487-111">Используйте [Connect-sposervice открывает](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) для подключения к центру администрирования географически расположение, где требуется добавить администратора географически. (Например, Connect-sposervice открываетhttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="01487-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="01487-112">Чтобы просмотреть существующие Администраторы географического расположения, выполните`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="01487-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="01487-113">Добавление пользователя в качестве администратора географически</span><span class="sxs-lookup"><span data-stu-id="01487-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="01487-114">Для добавления пользователя в качестве администратора географически, выполните`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="01487-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="01487-115">Чтобы удалить пользователя администратором географического расположения, выполните`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="01487-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="01487-116">Добавление группы в качестве администратора географически</span><span class="sxs-lookup"><span data-stu-id="01487-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="01487-117">Можно добавить группу безопасности или группу безопасности с включенной поддержкой почты как администратор географически. (Группы рассылки и группы Office 365 не поддерживаются).</span><span class="sxs-lookup"><span data-stu-id="01487-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="01487-118">Чтобы добавить группу от имени администратора географически, выполните`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="01487-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="01487-119">Чтобы удалить группу от имени администратора географически, выполните`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="01487-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="01487-p103">Обратите внимание, что не все группы безопасности псевдоним группы. Если вы хотите добавить группу безопасности, для которого не псевдоним, запустите [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) для получения списка групп, найдите группу безопасности ObjectID и выполните:</span><span class="sxs-lookup"><span data-stu-id="01487-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="01487-122">Чтобы удалить группу с помощью ObjectID, выполните`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="01487-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="01487-123">Доступ к центру администрирования для конкретного географического расположения</span><span class="sxs-lookup"><span data-stu-id="01487-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="01487-124">Для администрирования параметров OneDrive для их географического расположения, "Администраторы" необходимо получить доступ к центру администрирования OneDrive напрямую с помощью следующий формат URL-адреса:</span><span class="sxs-lookup"><span data-stu-id="01487-124">To administer OneDrive settings for their geo location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="01487-125">https://admin.onedrive.com/?geo=<*географическая*></span><span class="sxs-lookup"><span data-stu-id="01487-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="01487-126">К примеру, Центр администрирования OneDrive для Канады расположена в каталоге: https://admin.onedrive.com/?geo=CAN.</span><span class="sxs-lookup"><span data-stu-id="01487-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="01487-127">См. также</span><span class="sxs-lookup"><span data-stu-id="01487-127">See Also</span></span>

[<span data-ttu-id="01487-128">Добавление SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="01487-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="01487-129">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="01487-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="01487-130">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="01487-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="01487-131">Настройка псевдонима (MailNickName) для группы безопасности</span><span class="sxs-lookup"><span data-stu-id="01487-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)