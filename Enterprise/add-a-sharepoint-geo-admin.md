---
title: Добавление и удаление администратора геообъектов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: Узнайте, как добавить или удалить администратора геообъектов в Office 365 с поддержкой нескольких регионов.
ms.openlocfilehash: 54850252d133e3e26b02cabe3ead0900287e832c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490915"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a><span data-ttu-id="aff15-103">Добавление и удаление администратора геообъектов в Office 365 с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="aff15-103">Add or remove a geo administrator in Office 365 Multi-Geo</span></span>

<span data-ttu-id="aff15-104">Можно настроить отдельных администраторов для каждого географического расположения в клиенте.</span><span class="sxs-lookup"><span data-stu-id="aff15-104">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="aff15-105">Эти администраторы получат доступ к параметрам SharePoint Online и OneDrive, относящимся к конкретным географическим расположениям.</span><span class="sxs-lookup"><span data-stu-id="aff15-105">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="aff15-106">Некоторые службы, например банк терминов, управляются из центрального расположения и копируются в периферийные расположения.</span><span class="sxs-lookup"><span data-stu-id="aff15-106">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="aff15-107">Доступ к ним есть у администратора геообъектов в центральном расположении, но не у администраторов геообъектов в периферийных расположениях.</span><span class="sxs-lookup"><span data-stu-id="aff15-107">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="aff15-108">Глобальные администраторы и администраторы SharePoint Online сохраняют доступ к параметрам в центральном и всех периферийных расположениях.</span><span class="sxs-lookup"><span data-stu-id="aff15-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="aff15-109">Настройка администраторов геообъектов</span><span class="sxs-lookup"><span data-stu-id="aff15-109">Configuring geo administrators</span></span>

<span data-ttu-id="aff15-110">Для настройки администраторов геообъектов требуется модуль PowerShell в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="aff15-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="aff15-111">Используйте команду [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) для подключения к центру администрирования геообъекта, для которого нужно добавить администратора. (Например, Connect-SPOService https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="aff15-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="aff15-112">Чтобы просмотреть существующих администраторов геообъектов в расположении, выполните команду `Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="aff15-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="aff15-113">Добавление пользователя в качестве администратора геообъекта</span><span class="sxs-lookup"><span data-stu-id="aff15-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="aff15-114">Чтобы добавить пользователя в качестве администратора геообъекта, выполните команду `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="aff15-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="aff15-115">Чтобы удалить пользователя из администраторов геообъекта в расположении, выполните команду `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="aff15-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="aff15-116">Добавление группы в качестве администратора геообъекта</span><span class="sxs-lookup"><span data-stu-id="aff15-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="aff15-117">Можно добавить группу безопасности или группу безопасности с поддержкой электронной почты в качестве администратора геообъекта. (Группы рассылки и группы Office 365 не поддерживаются.)</span><span class="sxs-lookup"><span data-stu-id="aff15-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="aff15-118">Чтобы добавить группу в качестве администратора геообъекта, выполните команду `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="aff15-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="aff15-119">Чтобы удалить группу из администраторов геообъекта, выполните команду `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="aff15-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="aff15-120">Обратите внимание, что не у всех групп безопасности есть псевдоним группы.</span><span class="sxs-lookup"><span data-stu-id="aff15-120">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="aff15-121">Если нужно добавить группу безопасности без псевдонима, выполните команду [Get-MsolGroup](https://docs.microsoft.com/ru-RU/powershell/module/msonline/get-msolgroup) для получения списка групп, найдите ObjectID группы безопасности и выполните команду:</span><span class="sxs-lookup"><span data-stu-id="aff15-121">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/ru-RU/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="aff15-122">Чтобы удалить группу с помощью ObjectID, выполните команду `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="aff15-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="aff15-123">См. также</span><span class="sxs-lookup"><span data-stu-id="aff15-123">See Also</span></span>

[<span data-ttu-id="aff15-124">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="aff15-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="aff15-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="aff15-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="aff15-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="aff15-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="aff15-127">Установка псевдонима (MailNickName) для группы безопасности</span><span class="sxs-lookup"><span data-stu-id="aff15-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/ru-RU/powershell/module/azuread/set-azureadgroup)