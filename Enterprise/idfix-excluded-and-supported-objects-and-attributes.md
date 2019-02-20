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
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085088"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="39f54-103">Исключаемые и поддерживаемые объекты и атрибуты IdFix</span><span class="sxs-lookup"><span data-stu-id="39f54-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="39f54-p101">Существует два набора правил, поддерживаемых IdFix, — многопользовательский и выделенный/ITAR. В настоящее время эти два набора правил исключают из поиска одинаковые объекты, атрибуты и значения атрибутов. Это может измениться в последующих выпусках.</span><span class="sxs-lookup"><span data-stu-id="39f54-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="39f54-107">Многопользовательские и выделенные ошибочные исключения, используемые IdFix</span><span class="sxs-lookup"><span data-stu-id="39f54-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="39f54-p102">В этом разделе перечислены объекты, атрибуты и значения, которые IdFix исключает из поиска в каталоге. Звездочка (\*) — это подстановочный знак, который можно заменить на другие символы.</span><span class="sxs-lookup"><span data-stu-id="39f54-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="39f54-110">Объекты, атрибуты и значения, исключаемые во время поиска по IdFix</span><span class="sxs-lookup"><span data-stu-id="39f54-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="39f54-111">**Исключения**</span><span class="sxs-lookup"><span data-stu-id="39f54-111">**Exclusion**</span></span>|<span data-ttu-id="39f54-112">**Пример**</span><span class="sxs-lookup"><span data-stu-id="39f54-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="39f54-113">Админи\*</span><span class="sxs-lookup"><span data-stu-id="39f54-113">Admini\*</span></span> |<span data-ttu-id="39f54-114">Администратор</span><span class="sxs-lookup"><span data-stu-id="39f54-114">Administrator</span></span> |
|<span data-ttu-id="39f54-115">КАС_ {\*</span><span class="sxs-lookup"><span data-stu-id="39f54-115">CAS_{\*</span></span>  |<span data-ttu-id="39f54-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="39f54-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="39f54-117">Дисковерисеарчмаилбокс\*</span><span class="sxs-lookup"><span data-stu-id="39f54-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="39f54-118">Дисковерисеарчмаилбокс</span><span class="sxs-lookup"><span data-stu-id="39f54-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="39f54-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="39f54-119">FederatedEmail\*</span></span> |<span data-ttu-id="39f54-p103">FederatedEmail. *Идентификатор GUID*</span><span class="sxs-lookup"><span data-stu-id="39f54-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="39f54-122">Гость\*</span><span class="sxs-lookup"><span data-stu-id="39f54-122">Guest\*</span></span> ||
|<span data-ttu-id="39f54-123">Хттпконнектор\*</span><span class="sxs-lookup"><span data-stu-id="39f54-123">HTTPConnector\*</span></span>  |<span data-ttu-id="39f54-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="39f54-124">HTTPConnector</span></span> |
|<span data-ttu-id="39f54-125">KRBTGT\*</span><span class="sxs-lookup"><span data-stu-id="39f54-125">krbtgt\*</span></span> |<span data-ttu-id="39f54-126">MS DS: KrbTgt – Link</span><span class="sxs-lookup"><span data-stu-id="39f54-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="39f54-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="39f54-127">iusr_\*</span></span> |<span data-ttu-id="39f54-128">IUSR_ *имя_компьютера*</span><span class="sxs-lookup"><span data-stu-id="39f54-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="39f54-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="39f54-129">iwam\*</span></span>  |<span data-ttu-id="39f54-130">IWAM_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="39f54-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="39f54-131">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="39f54-131">msol\*</span></span> |<span data-ttu-id="39f54-132">МСОЛ_АД_СИНК</span><span class="sxs-lookup"><span data-stu-id="39f54-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="39f54-133">поддержки\*</span><span class="sxs-lookup"><span data-stu-id="39f54-133">support_\*</span></span> ||
|<span data-ttu-id="39f54-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="39f54-134">SystemMailbox\*</span></span> |<span data-ttu-id="39f54-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="39f54-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="39f54-136">Ввиоадмини\*</span><span class="sxs-lookup"><span data-stu-id="39f54-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="39f54-137">distinguishedName содержит "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="39f54-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="39f54-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="39f54-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="39f54-139">Объект содержит атрибут IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="39f54-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="39f54-140">Ознакомьтесь с [атрибутОм искритикалсистемобжект](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="39f54-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="39f54-141">Многопользовательские и выделенные объекты и атрибуты, проверяемые IdFix</span><span class="sxs-lookup"><span data-stu-id="39f54-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="39f54-142">Атрибуты, которые проверяются на наличие ошибок с помощью IdFix, описаны в разделе "объект каталога и подготовка атрибута" в разделе [Подготовка атрибутов каталога для синхронизации с Office 365 с помощью средства IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="39f54-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

