---
title: Исключаемые и поддерживаемые объекты и атрибуты IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
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
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487185"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="65888-103">Исключаемые и поддерживаемые объекты и атрибуты IdFix</span><span class="sxs-lookup"><span data-stu-id="65888-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="65888-104">Существует два набора правил, поддерживаемых IdFix; Поддержка нескольких клиентов и выделенного/ITAR.</span><span class="sxs-lookup"><span data-stu-id="65888-104">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="65888-105">В настоящее время два набора правил исключают одни и те же объекты, атрибуты и значения атрибутов из поиска.</span><span class="sxs-lookup"><span data-stu-id="65888-105">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="65888-106">Это может измениться в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="65888-106">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="65888-107">Несколько клиентов и выделенные исключения ошибок, используемые IdFix</span><span class="sxs-lookup"><span data-stu-id="65888-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="65888-108">В этом разделе перечислены объекты, атрибуты и значения, которые IdFix исключает из поиска в каталоге.</span><span class="sxs-lookup"><span data-stu-id="65888-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="65888-109">Звездочка (\*) — это подстановочный знак, который можно заменить на другие символы.</span><span class="sxs-lookup"><span data-stu-id="65888-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="65888-110">Объекты, атрибуты и значения, исключенные во время поиска IdFix</span><span class="sxs-lookup"><span data-stu-id="65888-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="65888-111">**Исключения**</span><span class="sxs-lookup"><span data-stu-id="65888-111">**Exclusion**</span></span>|<span data-ttu-id="65888-112">**Пример**</span><span class="sxs-lookup"><span data-stu-id="65888-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="65888-113">Админи\*</span><span class="sxs-lookup"><span data-stu-id="65888-113">Admini\*</span></span> |<span data-ttu-id="65888-114">Администратор</span><span class="sxs-lookup"><span data-stu-id="65888-114">Administrator</span></span> |
|<span data-ttu-id="65888-115">КАС_ {\*</span><span class="sxs-lookup"><span data-stu-id="65888-115">CAS_{\*</span></span>  |<span data-ttu-id="65888-116">КАС_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="65888-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="65888-117">Дисковерисеарчмаилбокс\*</span><span class="sxs-lookup"><span data-stu-id="65888-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="65888-118">Дисковерисеарчмаилбокс</span><span class="sxs-lookup"><span data-stu-id="65888-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="65888-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="65888-119">FederatedEmail\*</span></span> |<span data-ttu-id="65888-120">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="65888-120">FederatedEmail.</span></span> <span data-ttu-id="65888-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="65888-121">*GUID*</span></span> |
|<span data-ttu-id="65888-122">Guest\*</span><span class="sxs-lookup"><span data-stu-id="65888-122">Guest\*</span></span> ||
|<span data-ttu-id="65888-123">Хттпконнектор\*</span><span class="sxs-lookup"><span data-stu-id="65888-123">HTTPConnector\*</span></span>  |<span data-ttu-id="65888-124">Хттпконнектор</span><span class="sxs-lookup"><span data-stu-id="65888-124">HTTPConnector</span></span> |
|<span data-ttu-id="65888-125">KRBTGT\*</span><span class="sxs-lookup"><span data-stu-id="65888-125">krbtgt\*</span></span> |<span data-ttu-id="65888-126">MS DS: KrbTgt – Link</span><span class="sxs-lookup"><span data-stu-id="65888-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="65888-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="65888-127">iusr_\*</span></span> |<span data-ttu-id="65888-128">IUSR_ *имя_компьютера*</span><span class="sxs-lookup"><span data-stu-id="65888-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="65888-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="65888-129">iwam\*</span></span>  |<span data-ttu-id="65888-130">IWAM_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="65888-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="65888-131">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="65888-131">msol\*</span></span> |<span data-ttu-id="65888-132">МСОЛ_АД_СИНК</span><span class="sxs-lookup"><span data-stu-id="65888-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="65888-133">поддержки\*</span><span class="sxs-lookup"><span data-stu-id="65888-133">support_\*</span></span> ||
|<span data-ttu-id="65888-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="65888-134">SystemMailbox\*</span></span> |<span data-ttu-id="65888-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="65888-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="65888-136">Ввиоадмини\*</span><span class="sxs-lookup"><span data-stu-id="65888-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="65888-137">distinguishedName содержит "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="65888-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="65888-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="65888-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="65888-139">Объект содержит атрибут Искритикалсистемобжект</span><span class="sxs-lookup"><span data-stu-id="65888-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="65888-140">Ознакомьтесь с [атрибутОм искритикалсистемобжект](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="65888-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="65888-141">Поддержка нескольких клиентов и выделенных объектов и атрибутов, проверенных с помощью IdFix</span><span class="sxs-lookup"><span data-stu-id="65888-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="65888-142">Атрибуты, которые проверяются на наличие ошибок с помощью IdFix, описаны в разделе "объект каталога и подготовка атрибута" в разделе [Подготовка атрибутов каталога для синхронизации с Office 365 с помощью средства IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="65888-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

