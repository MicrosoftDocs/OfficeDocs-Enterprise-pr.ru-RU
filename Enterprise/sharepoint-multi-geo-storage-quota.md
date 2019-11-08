---
title: Квоты хранилища SharePoint в средах с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Сведения о квотах хранилища SharePoint в средах с поддержкой нескольких регионов.
ms.openlocfilehash: d4049312a2da64f16d2637ffd37adf98f2282287
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033385"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="525e2-103">Квоты хранилища SharePoint в средах с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="525e2-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="525e2-104">По умолчанию все регионы среды с поддержкой нескольких регионов совместно используют доступную квоту хранилища клиента.</span><span class="sxs-lookup"><span data-stu-id="525e2-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="525e2-105">С помощью параметра квоты хранилища географического расположения SharePoint можно управлять квотой хранилища для каждого географического расположения.</span><span class="sxs-lookup"><span data-stu-id="525e2-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="525e2-106">При выделении квоты хранилища для географического расположения она определяет максимальный объем дискового пространства, доступного для этого географического расположения, и вычитается из доступного дискового пространства клиента.</span><span class="sxs-lookup"><span data-stu-id="525e2-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="525e2-107">Оставшееся доступное дисковое пространство клиента затем делится между настроенными географическими расположениями, для которых не выделены определенные квоты хранилища.</span><span class="sxs-lookup"><span data-stu-id="525e2-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="525e2-108">Квота хранилища SharePoint для любого географического расположения может быть выделена администратором SharePoint Online путем подключения к центральному расположению.</span><span class="sxs-lookup"><span data-stu-id="525e2-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="525e2-109">Администраторы геообъектов для периферийных расположений могут просматривать квоту хранилища, но не могут ее выделять.</span><span class="sxs-lookup"><span data-stu-id="525e2-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="525e2-110">Настройка квоты хранилища для географического расположения</span><span class="sxs-lookup"><span data-stu-id="525e2-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="525e2-111">Используйте [модуль Microsoft SharePoint Online](https://www.microsoft.com/download/details.aspx?id=35588 ) и подключитесь к центральному расположению, чтобы выделить квоту хранилища для географического расположения.</span><span class="sxs-lookup"><span data-stu-id="525e2-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/download/details.aspx?id=35588 ) and connect to the central location to allocate the storage quota for a geo location.</span></span> 

<span data-ttu-id="525e2-112">Чтобы выделить квоту хранилища для расположения, выполните следующий командлет:</span><span class="sxs-lookup"><span data-stu-id="525e2-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

<span data-ttu-id="525e2-113">Чтобы просмотреть квоту хранилища для текущего географического расположения, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="525e2-113">To view Storage Quota for the current geo location, run:</span></span>

`Get-SPOGeoStorageQuota`

![Снимок экрана: окно PowerShell с командлетом Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

<span data-ttu-id="525e2-115">Чтобы просмотреть квоту хранилища для всех географических расположений, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="525e2-115">To view Storage Quota for all geo locations, run:</span></span>

`Get-SPOGeoStorageQuota -AllLocations`

<span data-ttu-id="525e2-116">Чтобы удалить квоту хранилища, выделенную для географического расположения, установите параметр `StorageQuota value = 0`:</span><span class="sxs-lookup"><span data-stu-id="525e2-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
