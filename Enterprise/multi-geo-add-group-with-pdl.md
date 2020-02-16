---
title: Создание группы Office 365 с определенным предпочтительным расположением данных (PDL)
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Узнайте, как создать группу Office 365 с указанным предпочтительным расположением данных в среде с поддержкой нескольких регионов.
ms.openlocfilehash: 96c2e5513879dff291c0119ddad38a78ab91ec1a
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974091"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="d9193-103">Создание группы Office 365 с определенным предпочтительным расположением данных (PDL)</span><span class="sxs-lookup"><span data-stu-id="d9193-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="d9193-104">Когда пользователь в среде с поддержкой нескольких регионов создает группу Office 365, предпочтительному расположению данных группы автоматически присваивается значение, соответствующее этому значению пользователя.</span><span class="sxs-lookup"><span data-stu-id="d9193-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="d9193-105">Глобальные администраторы, администраторы SharePoint и Exchange могут создавать группы в любом выбранном регионе.</span><span class="sxs-lookup"><span data-stu-id="d9193-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="d9193-106">Если нужно создать группу с определенным PDL, можно использовать Центр администрирования SharePoint или командлет Microsoft PowerShell New-UnifiedGroup для Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="d9193-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="d9193-107">При этом как почтовый ящик группы, так и сайт SharePoint, связанный с группой, подготавливаются в указанном предпочтительном расположении данных (PDL).</span><span class="sxs-lookup"><span data-stu-id="d9193-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="d9193-108">Чтобы создать группу Office 365 с указанным PDL, перейдите в Центр администрирования SharePoint в географическом расположении, где нужно создать сайт группы.</span><span class="sxs-lookup"><span data-stu-id="d9193-108">To create an Office 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="d9193-109">Пример:</span><span class="sxs-lookup"><span data-stu-id="d9193-109">For example:</span></span>

<span data-ttu-id="d9193-110">Если нужно создать сайт группы в Австралии, вы можете перейти на страницу https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span><span class="sxs-lookup"><span data-stu-id="d9193-110">If you wan to create a group site in your Australtia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="d9193-111">Нажмите **+ Создать**.</span><span class="sxs-lookup"><span data-stu-id="d9193-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="d9193-112">Следуйте инструкциям, чтобы создать сайт группы.</span><span class="sxs-lookup"><span data-stu-id="d9193-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="d9193-113">Сайт группы будет подготовлен в географическом расположении, соответствующем Центру администрирования SharePoint, из которого вы отправили запрос на создание сайта.</span><span class="sxs-lookup"><span data-stu-id="d9193-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="d9193-114">Использование Exchange PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9193-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="d9193-115">Подключитесь к Exchange Online PowerShell и передайте параметр *- MailBoxRegion* с кодом региона.</span><span class="sxs-lookup"><span data-stu-id="d9193-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="d9193-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="d9193-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Снимок экрана: командлет PowerShell New-UnifiedGroup с синтаксисом](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="d9193-118">Обратите внимание, что подготовка сайта группы SharePoint выполняется по запросу.</span><span class="sxs-lookup"><span data-stu-id="d9193-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="d9193-119">В первый раз сайт будет подготовлен владельцем группы или участником, пытающимся получить к нему доступ.</span><span class="sxs-lookup"><span data-stu-id="d9193-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="d9193-120">Коды регионов</span><span class="sxs-lookup"><span data-stu-id="d9193-120">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="d9193-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d9193-121">See also</span></span>

[<span data-ttu-id="d9193-122">Подключение к PowerShell Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d9193-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
