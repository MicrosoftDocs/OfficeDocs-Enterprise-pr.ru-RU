---
title: Исключаемые и поддерживаемые объекты и атрибуты IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Список атрибутов, исключаемых и поддерживаемых средством IdFix.
ms.openlocfilehash: e57507688fe1efd21bb629b4fad297129eff55d6
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813929"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="8545e-103">Исключаемые и поддерживаемые объекты и атрибуты IdFix</span><span class="sxs-lookup"><span data-stu-id="8545e-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="8545e-104">*Эта статья относится к Office 365 корпоративный и Microsoft 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="8545e-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="8545e-105">Существует два набора правил, поддерживаемых IdFix; Поддержка нескольких клиентов и выделенного/ITAR.</span><span class="sxs-lookup"><span data-stu-id="8545e-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="8545e-106">В настоящее время два набора правил исключают одни и те же объекты, атрибуты и значения атрибутов из поиска.</span><span class="sxs-lookup"><span data-stu-id="8545e-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="8545e-107">Это может измениться в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="8545e-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="8545e-108">Несколько клиентов и выделенные исключения ошибок, используемые IdFix</span><span class="sxs-lookup"><span data-stu-id="8545e-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="8545e-109">В этом разделе перечислены объекты, атрибуты и значения, которые IdFix исключает из поиска в каталоге.</span><span class="sxs-lookup"><span data-stu-id="8545e-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="8545e-110">Звездочка (\*) — это подстановочный знак, который можно заменить на другие символы.</span><span class="sxs-lookup"><span data-stu-id="8545e-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="8545e-111">Объекты, атрибуты и значения, исключенные во время поиска IdFix</span><span class="sxs-lookup"><span data-stu-id="8545e-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="8545e-112">**Исключения**</span><span class="sxs-lookup"><span data-stu-id="8545e-112">**Exclusion**</span></span>|<span data-ttu-id="8545e-113">**Пример**</span><span class="sxs-lookup"><span data-stu-id="8545e-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8545e-114">админи\*</span><span class="sxs-lookup"><span data-stu-id="8545e-114">Admini\*</span></span> |<span data-ttu-id="8545e-115">Администратор</span><span class="sxs-lookup"><span data-stu-id="8545e-115">Administrator</span></span> |
|<span data-ttu-id="8545e-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="8545e-116">CAS_{\*</span></span>  |<span data-ttu-id="8545e-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="8545e-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="8545e-118">дисковерисеарчмаилбокс\*</span><span class="sxs-lookup"><span data-stu-id="8545e-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="8545e-119">дисковерисеарчмаилбокс</span><span class="sxs-lookup"><span data-stu-id="8545e-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="8545e-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="8545e-120">FederatedEmail\*</span></span> |<span data-ttu-id="8545e-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="8545e-121">FederatedEmail.</span></span> <span data-ttu-id="8545e-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="8545e-122">*GUID*</span></span> |
|<span data-ttu-id="8545e-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="8545e-123">Guest\*</span></span> ||
|<span data-ttu-id="8545e-124">хттпконнектор\*</span><span class="sxs-lookup"><span data-stu-id="8545e-124">HTTPConnector\*</span></span>  |<span data-ttu-id="8545e-125">хттпконнектор</span><span class="sxs-lookup"><span data-stu-id="8545e-125">HTTPConnector</span></span> |
|<span data-ttu-id="8545e-126">KRBTGT\*</span><span class="sxs-lookup"><span data-stu-id="8545e-126">krbtgt\*</span></span> |<span data-ttu-id="8545e-127">MS DS: KrbTgt – Link</span><span class="sxs-lookup"><span data-stu-id="8545e-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="8545e-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="8545e-128">iusr_\*</span></span> |<span data-ttu-id="8545e-129">iusr_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="8545e-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="8545e-130">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="8545e-130">iwam\*</span></span>  |<span data-ttu-id="8545e-131">IWAM_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="8545e-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="8545e-132">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="8545e-132">msol\*</span></span> |<span data-ttu-id="8545e-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="8545e-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="8545e-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="8545e-134">support_\*</span></span> ||
|<span data-ttu-id="8545e-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="8545e-135">SystemMailbox\*</span></span> |<span data-ttu-id="8545e-136">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="8545e-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="8545e-137">ввиоадмини\*</span><span class="sxs-lookup"><span data-stu-id="8545e-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="8545e-138">distinguishedName содержит "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="8545e-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="8545e-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="8545e-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="8545e-140">Объект содержит атрибут Искритикалсистемобжект</span><span class="sxs-lookup"><span data-stu-id="8545e-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="8545e-141">Ознакомьтесь с [атрибутом искритикалсистемобжект](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="8545e-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="8545e-142">Поддержка нескольких клиентов и выделенных объектов и атрибутов, проверенных с помощью IdFix</span><span class="sxs-lookup"><span data-stu-id="8545e-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="8545e-143">Атрибуты, которые проверяются на наличие ошибок с помощью IdFix, описаны в разделе "объект каталога и подготовка атрибута" в разделе [Подготовка атрибутов каталога для синхронизации с Office 365 с помощью средства IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="8545e-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

