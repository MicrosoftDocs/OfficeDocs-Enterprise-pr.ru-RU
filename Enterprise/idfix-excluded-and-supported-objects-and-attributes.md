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
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Содержит атрибуты, исключаемые и поддерживаемые инструмент IdFix.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542454"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="4d3e7-103">Исключаемые и поддерживаемые объекты и атрибуты IdFix</span><span class="sxs-lookup"><span data-stu-id="4d3e7-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="4d3e7-p101">Существует два набора правил, поддерживаемых IdFix, — многопользовательский и выделенный/ITAR. В настоящее время эти два набора правил исключают из поиска одинаковые объекты, атрибуты и значения атрибутов. Это может измениться в последующих выпусках.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="4d3e7-107">Многопользовательские и выделенные ошибочные исключения, используемые IdFix</span><span class="sxs-lookup"><span data-stu-id="4d3e7-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="4d3e7-p102">В этом разделе перечислены объекты, атрибуты и значения, которые IdFix исключает из поиск каталога. Символ звездочки (\*) — это подстановочный знак, который может быть заменен других знаков.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="4d3e7-110">Объекты, атрибуты и значения, исключаемые во время поиска по IdFix</span><span class="sxs-lookup"><span data-stu-id="4d3e7-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="4d3e7-111">**Исключения**</span><span class="sxs-lookup"><span data-stu-id="4d3e7-111">**Exclusion**</span></span>|<span data-ttu-id="4d3e7-112">**Пример**</span><span class="sxs-lookup"><span data-stu-id="4d3e7-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4d3e7-113">Уязвимой\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-113">Admini\*</span></span> |<span data-ttu-id="4d3e7-114">Администратор</span><span class="sxs-lookup"><span data-stu-id="4d3e7-114">Administrator</span></span> |
|<span data-ttu-id="4d3e7-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-115">CAS_{\*</span></span>  |<span data-ttu-id="4d3e7-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="4d3e7-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="4d3e7-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="4d3e7-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="4d3e7-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="4d3e7-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-119">FederatedEmail\*</span></span> |<span data-ttu-id="4d3e7-p103">FederatedEmail. *Идентификатор GUID*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="4d3e7-122">Гостевая\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-122">Guest\*</span></span> ||
|<span data-ttu-id="4d3e7-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-123">HTTPConnector\*</span></span>  |<span data-ttu-id="4d3e7-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-124">HTTPConnector</span></span> |
|<span data-ttu-id="4d3e7-125">KRBTGT\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-125">krbtgt\*</span></span> |<span data-ttu-id="4d3e7-126">MS-доменных служб Active Directory KrbTgt ссылки</span><span class="sxs-lookup"><span data-stu-id="4d3e7-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="4d3e7-127">IUSR_\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-127">iusr_\*</span></span> |<span data-ttu-id="4d3e7-128">IUSR_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="4d3e7-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-129">iwam\*</span></span>  |<span data-ttu-id="4d3e7-130">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="4d3e7-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-131">msol\*</span></span> |<span data-ttu-id="4d3e7-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="4d3e7-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="4d3e7-133">Support_\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-133">support_\*</span></span> ||
|<span data-ttu-id="4d3e7-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-134">SystemMailbox\*</span></span> |<span data-ttu-id="4d3e7-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="4d3e7-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="4d3e7-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="4d3e7-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="4d3e7-137">Различающееся_имя содержит «\0ACNF:»</span><span class="sxs-lookup"><span data-stu-id="4d3e7-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="4d3e7-138">«\0ACNF: *идентификатор GUID* "</span><span class="sxs-lookup"><span data-stu-id="4d3e7-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="4d3e7-139">Объект содержит атрибут IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="4d3e7-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="4d3e7-140">В разделе [атрибут isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="4d3e7-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="4d3e7-141">Многопользовательские и выделенные объекты и атрибуты, проверяемые IdFix</span><span class="sxs-lookup"><span data-stu-id="4d3e7-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="4d3e7-142">Атрибуты, которые проверяются на наличие ошибок с IdFix, описаны в разделе «каталог подготовки объектов и атрибутов» в [Подготовка атрибутов каталога для синхронизации с Office 365 с помощью инструмента IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="4d3e7-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

