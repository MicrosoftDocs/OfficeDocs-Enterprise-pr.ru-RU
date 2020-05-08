---
title: Создание группы Microsoft 365 с определенным предпочтительным расположением данных (PDL)
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
description: Узнайте, как создать группу Microsoft 365 с указанным предпочтительным расположением данных в среде с поддержкой нескольких регионов.
ms.openlocfilehash: 5b2294ff8821e84cb0158fa989b97134353969b2
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057989"
---
# <a name="create-an-microsoft-365-group-with-a-specific-pdl"></a><span data-ttu-id="59b05-103">Создание группы Microsoft 365 с определенным предпочтительным расположением данных (PDL)</span><span class="sxs-lookup"><span data-stu-id="59b05-103">Create an Microsoft 365 Group with a specific PDL</span></span>

<span data-ttu-id="59b05-104">Когда пользователь в среде с поддержкой нескольких регионов создает группу Microsoft 365, предпочтительному расположению данных группы автоматически присваивается значение, соответствующее расположению данных пользователя.</span><span class="sxs-lookup"><span data-stu-id="59b05-104">When users in a multi-geo environment create an Microsoft 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="59b05-105">Глобальные администраторы, администраторы SharePoint и Exchange могут создавать группы в любом выбранном регионе.</span><span class="sxs-lookup"><span data-stu-id="59b05-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="59b05-106">Если нужно создать группу с определенным PDL, можно использовать Центр администрирования SharePoint или командлет Microsoft PowerShell New-UnifiedGroup для Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="59b05-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="59b05-107">При этом как почтовый ящик группы, так и сайт SharePoint, связанный с группой, подготавливаются в указанном предпочтительном расположении данных (PDL).</span><span class="sxs-lookup"><span data-stu-id="59b05-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="59b05-108">Чтобы создать группу Microsoft 365 с указанным PDL, перейдите в Центр администрирования SharePoint в географическом расположении, где нужно создать сайт группы.</span><span class="sxs-lookup"><span data-stu-id="59b05-108">To create an Microsoft 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="59b05-109">Пример:</span><span class="sxs-lookup"><span data-stu-id="59b05-109">For example:</span></span>

<span data-ttu-id="59b05-110">Если нужно создать сайт группы в Австралии, вы можете перейти на страницу https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span><span class="sxs-lookup"><span data-stu-id="59b05-110">If you want to create a group site in your Australia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="59b05-111">Нажмите **+ Создать**.</span><span class="sxs-lookup"><span data-stu-id="59b05-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="59b05-112">Следуйте инструкциям, чтобы создать сайт группы.</span><span class="sxs-lookup"><span data-stu-id="59b05-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="59b05-113">Сайт группы будет подготовлен в географическом расположении, соответствующем Центру администрирования SharePoint, из которого вы отправили запрос на создание сайта.</span><span class="sxs-lookup"><span data-stu-id="59b05-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="59b05-114">Использование Exchange PowerShell</span><span class="sxs-lookup"><span data-stu-id="59b05-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="59b05-115">Подключитесь к Exchange Online PowerShell и передайте параметр *- MailBoxRegion* с кодом региона.</span><span class="sxs-lookup"><span data-stu-id="59b05-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="59b05-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="59b05-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Снимок экрана: командлет PowerShell New-UnifiedGroup с синтаксисом](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="59b05-118">Обратите внимание, что подготовка сайта группы SharePoint выполняется по запросу.</span><span class="sxs-lookup"><span data-stu-id="59b05-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="59b05-119">В первый раз сайт будет подготовлен владельцем группы или участником, пытающимся получить к нему доступ.</span><span class="sxs-lookup"><span data-stu-id="59b05-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="59b05-120">Коды регионов</span><span class="sxs-lookup"><span data-stu-id="59b05-120">Geo location codes</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="59b05-121">См. также</span><span class="sxs-lookup"><span data-stu-id="59b05-121">See also</span></span>

[<span data-ttu-id="59b05-122">Подключение к PowerShell Exchange Online</span><span class="sxs-lookup"><span data-stu-id="59b05-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
