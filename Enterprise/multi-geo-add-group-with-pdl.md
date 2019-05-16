---
title: Создание группы Office 365 с определенным предпочтительным расположением данных (PDL)
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Узнайте, как создать группу Office 365 с указанным предпочтительным расположением данных в среде с поддержкой нескольких регионов.
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070006"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="a9e81-103">Создание группы Office 365 с определенным предпочтительным расположением данных (PDL)</span><span class="sxs-lookup"><span data-stu-id="a9e81-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="a9e81-104">Когда пользователь в среде с поддержкой нескольких регионов создает группу Office 365, предпочтительному расположению данных группы автоматически присваивается значение, соответствующее этому значению пользователя.</span><span class="sxs-lookup"><span data-stu-id="a9e81-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="a9e81-105">Если нужно создать группу с определенным PDL, можно использовать командлет Microsoft PowerShell New-UnifiedGroup для Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="a9e81-105">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="a9e81-106">При этом как почтовый ящик группы, так и сайт SharePoint, связанный с группой, подготавливаются в указанном предпочтительном расположении данных (PDL).</span><span class="sxs-lookup"><span data-stu-id="a9e81-106">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="a9e81-107">Для выполнения этого действия нужно быть глобальным администратором или администратором SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a9e81-107">You must be a global administrator or a SharePoint Online or Exchange Online administrator to do this.</span></span>

<span data-ttu-id="a9e81-108">Чтобы создать группу Office 365 с указанным PDL, подключитесь к Exchange Online PowerShell и передайте параметр *- MailBoxRegion* с кодом региона.</span><span class="sxs-lookup"><span data-stu-id="a9e81-108">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="a9e81-109">Пример:</span><span class="sxs-lookup"><span data-stu-id="a9e81-109">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Снимок экрана: командлет PowerShell New-UnifiedGroup с синтаксисом](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="a9e81-111">Обратите внимание, что подготовка сайта группы SharePoint выполняется по запросу.</span><span class="sxs-lookup"><span data-stu-id="a9e81-111">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="a9e81-112">В первый раз сайт будет подготовлен владельцем группы или участником, пытающимся получить к нему доступ.</span><span class="sxs-lookup"><span data-stu-id="a9e81-112">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="a9e81-113">Коды регионов</span><span class="sxs-lookup"><span data-stu-id="a9e81-113">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="a9e81-114">См. также</span><span class="sxs-lookup"><span data-stu-id="a9e81-114">See also</span></span>

[<span data-ttu-id="a9e81-115">Подключение к PowerShell Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a9e81-115">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)