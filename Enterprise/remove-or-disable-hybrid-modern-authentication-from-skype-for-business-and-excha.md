---
title: Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: При включении гибридного современных проверки подлинности (НЕГО) обнаружить, что она не подходит для текущей среды можно отключить НЕГО. В этой статье объясняется, как.
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542547"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="30d82-104">Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение</span><span class="sxs-lookup"><span data-stu-id="30d82-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="30d82-p102">При включении гибридного современных проверки подлинности (НЕГО) обнаружить, что она не подходит для текущей среды можно отключить НЕГО. В этой статье объясняется, как.</span><span class="sxs-lookup"><span data-stu-id="30d82-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="30d82-107">Для кого предназначена эта статья?</span><span class="sxs-lookup"><span data-stu-id="30d82-107">Who is this article for?</span></span>

<span data-ttu-id="30d82-108">Если были включены современных проверки подлинности в Скайп для бизнеса в Интернет или локальной, и/или Exchange Online или локальной и найдено необходимо отключить НЕГО, эти действия будут автоматически.</span><span class="sxs-lookup"><span data-stu-id="30d82-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>
  
 <span data-ttu-id="30d82-109">**Важные** В статье « [Скайп для бизнеса топологии, поддерживаемые с проверкой подлинности на современном](https://technet.microsoft.com/en-us/library/mt803262.aspx)» во время Скайп для бизнеса в Интернет или локальной, у НЕГО mixed топологии и обратите внимание на поддерживаемые топологии, прежде чем приступить к работе.</span><span class="sxs-lookup"><span data-stu-id="30d82-109">**Important** See the ' [Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="30d82-110">Как отключить современных проверки подлинности гибридной (Exchange)</span><span class="sxs-lookup"><span data-stu-id="30d82-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="30d82-111">**Локальную систему Exchange**: Откройте командную консоль Exchange и выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="30d82-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following command.</span></span> 
    
1. <span data-ttu-id="30d82-112">SET-OrganizationConfig-OAuth2ClientProfileEnabled $false</span><span class="sxs-lookup"><span data-stu-id="30d82-112">Set-OrganizationConfig -OAuth2ClientProfileEnabled $false</span></span>
    
2. <span data-ttu-id="30d82-113">SET-AuthServer-Identity evoSTS - IsDefaultAuthorizationEndpoint $false</span><span class="sxs-lookup"><span data-stu-id="30d82-113">Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false</span></span>
    
2. <span data-ttu-id="30d82-p103">**Exchange Online**: подключение к Exchange Online с помощью удаленной оболочки PowerShell. Выполните следующую команду, чтобы включить флага *OAuth2ClientProfileEnabled* значение «false».</span><span class="sxs-lookup"><span data-stu-id="30d82-p103">**Exchange Online**: Connect to Exchange Online with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false'.</span></span> 
    
1. <span data-ttu-id="30d82-116">SET-OrganizationConfig-OAuth2ClientProfileEnabled: $false</span><span class="sxs-lookup"><span data-stu-id="30d82-116">Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false</span></span>
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="30d82-117">Как отключить современных проверки подлинности гибридной (Скайп для бизнеса)</span><span class="sxs-lookup"><span data-stu-id="30d82-117">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="30d82-118">**Скайп для бизнеса в локальной**: выполните следующие команды в Скайп оболочки управления бизнеса.</span><span class="sxs-lookup"><span data-stu-id="30d82-118">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell.</span></span>
    
1. <span data-ttu-id="30d82-119">SET-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity «»</span><span class="sxs-lookup"><span data-stu-id="30d82-119">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""</span></span>
    
2. <span data-ttu-id="30d82-p104">**Скайп для бизнеса в Интернете**: подключение к Скайп для бизнеса через Интернет с помощью удаленной оболочки PowerShell. Выполните следующую команду для отключения современных проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="30d82-p104">**Skype for Business Online**: Connect to Skype for Business Online with Remote PowerShell. Run the following command to disable Modern Authentication.</span></span> 
    
1. <span data-ttu-id="30d82-122">SET-CsOAuthConfiguration - ClientAdalAuthOverride не разрешены</span><span class="sxs-lookup"><span data-stu-id="30d82-122">Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed</span></span>
    
<span data-ttu-id="30d82-123">[Ссылку на обзор современного проверки подлинности](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="30d82-123">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

