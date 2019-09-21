---
title: Пределы ресурсов для Office 365
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
description: Сводка. сведения об ограничении ресурсов для различных приложений в Office 365.
ms.openlocfilehash: ece25deece5a0f2eec7ab0295a2af68f47e1c50c
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067757"
---
# <a name="resource-limits"></a><span data-ttu-id="23b14-103">Ограничения ресурсов</span><span class="sxs-lookup"><span data-stu-id="23b14-103">Resource Limits</span></span>

<span data-ttu-id="23b14-104">Ограничения ресурсов применяются с помощью квот (ограничений) и регулирования.</span><span class="sxs-lookup"><span data-stu-id="23b14-104">Resource limits are enforced using quotas (limits) and throttling.</span></span> <span data-ttu-id="23b14-105">Azure Active Directory и отдельные службы Office 365 используют оба.</span><span class="sxs-lookup"><span data-stu-id="23b14-105">Azure Active Directory and the individual Office 365 services use both.</span></span> <span data-ttu-id="23b14-106">При добавлении новых возможностей предельные значения задаются для конкретных служб и изменяются с течением времени.</span><span class="sxs-lookup"><span data-stu-id="23b14-106">Limits are service-specific and change over time as new capabilities are added.</span></span> <span data-ttu-id="23b14-107">Сведения о текущих пределах для различных служб представлены в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="23b14-107">For details on the current limits for the various services, see the following topics:</span></span>
- [<span data-ttu-id="23b14-108">Ограничения и ограничения для службы Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="23b14-108">Azure Active Directory service limits and restrictions</span></span>](https://msdn.microsoft.com/en-us/library/azure/dn764971.aspx)
- [<span data-ttu-id="23b14-109">Ограничения Exchange Online</span><span class="sxs-lookup"><span data-stu-id="23b14-109">Exchange Online Limits</span></span>](https://technet.microsoft.com/en-us/library/exchange-online-limits.aspx)
- [<span data-ttu-id="23b14-110">Ограничения Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="23b14-110">Exchange Online Protection Limits</span></span>](https://technet.microsoft.com/en-us/library/exchange-online-protection-limits.aspx)
- [<span data-ttu-id="23b14-111">Границы и ограничения программного обеспечения SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="23b14-111">SharePoint Online software boundaries and limits</span></span>](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [<span data-ttu-id="23b14-112">Пределы Skype для бизнеса</span><span class="sxs-lookup"><span data-stu-id="23b14-112">Skype for Business Limits</span></span>](https://technet.microsoft.com/en-us/library/skype-for-business-online-limits.aspx)
- [<span data-ttu-id="23b14-113">API REST для REST и пределы скорости</span><span class="sxs-lookup"><span data-stu-id="23b14-113">Yammer REST API and Rate Limits</span></span>](https://developer.yammer.com/docs/rest-api-rate-limits)
- [<span data-ttu-id="23b14-114">Предельные значения для размера файлов в Sway</span><span class="sxs-lookup"><span data-stu-id="23b14-114">File Size Limits in Sway</span></span>](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

<span data-ttu-id="23b14-115">В дополнение к этим ограничениям в Azure Active Directory и Office 365 используются несколько механизмов регулирования.</span><span class="sxs-lookup"><span data-stu-id="23b14-115">In addition to these limits, several throttling mechanisms are used throughout Azure Active Directory and Office 365.</span></span> <span data-ttu-id="23b14-116">Регулирование в службе особенно важно, так как сетевые ресурсы в центрах обработки данных корпорации Майкрософт оптимизированы для широкого набора клиентов, использующих эти службы.</span><span class="sxs-lookup"><span data-stu-id="23b14-116">Throttling within the service is especially important, given that network resources in Microsoft's datacenters are optimized for the broad set of customers that use the services.</span></span> <span data-ttu-id="23b14-117">Механизмы регулирования включают:</span><span class="sxs-lookup"><span data-stu-id="23b14-117">Throttling mechanisms include:</span></span>
- <span data-ttu-id="23b14-118">Функция регулирования на уровне пользователей Azure Active Directory и Office 365, которая ограничивает количество транзакций или одновременных вызовов (в соответствии со сценарием или кодом), которые могут выполняться одним пользователем.</span><span class="sxs-lookup"><span data-stu-id="23b14-118">Azure Active Directory and Office 365 feature user-level throttling, which limit the number of transactions or concurrent calls (by script or code) that can be performed by a single user.</span></span>
- <span data-ttu-id="23b14-119">Политика регулирования PowerShell по умолчанию назначается каждому клиенту при создании клиента.</span><span class="sxs-lookup"><span data-stu-id="23b14-119">A default PowerShell throttling policy is assigned to each tenant at tenant creation.</span></span> <span data-ttu-id="23b14-120">Эти параметры влияют на другие элементы, например максимальное количество одновременных сеансов PowerShell, которые могут быть открыты одним администратором.</span><span class="sxs-lookup"><span data-stu-id="23b14-120">These settings affect other items, such as the maximum number of simultaneous PowerShell sessions that can be opened by a single administrator.</span></span>
- <span data-ttu-id="23b14-121">У каждого клиента Exchange Online есть политика веб-служб Exchange по умолчанию (EWS), которая настроена на выполнение клиентских операций EWS, и регулирование, которое применяется ко всем клиентам Outlook.</span><span class="sxs-lookup"><span data-stu-id="23b14-121">Each Exchange Online customer has a default Exchange Web Services (EWS) policy that is tuned for EWS client operations, and throttling that applies to all Outlook clients.</span></span>
