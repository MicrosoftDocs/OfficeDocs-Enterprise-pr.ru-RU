---
title: Элементы управления доступом к Office 365 Yammer корпоративный
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Сводка. Краткие сведения об элементах управления корпоративным доступом в Yammer в рабочей среде.
ms.openlocfilehash: 9b88ff0f8c480dd3726246e47714d9468509ef08
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841796"
---
# <a name="yammer-enterprise-access-controls"></a><span data-ttu-id="b33dc-103">Элементы управления доступом к Yammer корпоративный</span><span class="sxs-lookup"><span data-stu-id="b33dc-103">Yammer Enterprise Access Controls</span></span> 

<span data-ttu-id="b33dc-104">Физический и логический доступ к рабочей среде Yammer ограничена небольшим набором людей (инфраструктура и операции).</span><span class="sxs-lookup"><span data-stu-id="b33dc-104">Physical and logical access to the Yammer production environment is restricted to a small set of people (infrastructure and operations).</span></span> <span data-ttu-id="b33dc-105">Как и в случае с другими инженерами Office 365, инженеры Yammer имеют нулевой доступ к данным клиента.</span><span class="sxs-lookup"><span data-stu-id="b33dc-105">As with other Office 365 engineers, Yammer engineers have zero standing access to Customer Data.</span></span> <span data-ttu-id="b33dc-106">Доступ должен быть запрошен с помощью системы управления доступом на основе утверждений, как и для защищенного хранилища, с ограниченным количеством утверждающих.</span><span class="sxs-lookup"><span data-stu-id="b33dc-106">Access must be requested using an approval-based just-in-time access control system similar to Lockbox with a limited number of approvers.</span></span> <span data-ttu-id="b33dc-107">Утверждающие проверяют запрос (например, проверяют, является ли запрос действительным на основании потребностей, Бизнес-дел, времени и т. д.), а затем Утвердите или отклоните запрос.</span><span class="sxs-lookup"><span data-stu-id="b33dc-107">Approvers verify the request (for example, they verify whether the request is legitimate based on need, business case, time, etc.), and then approve or deny the request.</span></span> <span data-ttu-id="b33dc-108">Если запрос утвержден, JIT-доступ предоставляется для определенного и ограниченного времени.</span><span class="sxs-lookup"><span data-stu-id="b33dc-108">If the request is approved, JIT access is granted for a defined and limited time.</span></span> <span data-ttu-id="b33dc-109">После превышения времени доступа срок действия доступа истекает автоматически.</span><span class="sxs-lookup"><span data-stu-id="b33dc-109">After access time is exceeded, the access automatically expires.</span></span>

<span data-ttu-id="b33dc-110">Как и в случае с другими службами Office 365, все доступ к рабочей среде Yammer использует многофакторную проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="b33dc-110">As with other Office 365 services, all access to the Yammer production environment uses multi-factor authentication.</span></span> <span data-ttu-id="b33dc-111">Все пользователи получают доступ к журналу команд и записываются в журнал и регулярно проверяются группой безопасности Yammer.</span><span class="sxs-lookup"><span data-stu-id="b33dc-111">All access and command history is attributed to a user, and logged and reviewed regularly by the Yammer security team.</span></span>

<span data-ttu-id="b33dc-112">Для получения дополнительных сведений об администрировании и управлении Yammer обратитесь к [справочной статье администратора Yammer](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).</span><span class="sxs-lookup"><span data-stu-id="b33dc-112">For more information about Yammer administration and management, see [Yammer Admin Help](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).</span></span>