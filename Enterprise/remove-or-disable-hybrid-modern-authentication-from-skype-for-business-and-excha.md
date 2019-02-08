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
ms.openlocfilehash: 802add6295edffe3ec80e70e9bd70663479ec61a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "25359031"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="9c704-104">Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение</span><span class="sxs-lookup"><span data-stu-id="9c704-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="9c704-p102">При включении гибридного современных проверки подлинности (НЕГО) обнаружить, что она не подходит для текущей среды можно отключить НЕГО. В этой статье объясняется, как.</span><span class="sxs-lookup"><span data-stu-id="9c704-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="9c704-107">Для кого предназначена эта статья?</span><span class="sxs-lookup"><span data-stu-id="9c704-107">Who is this article for?</span></span>

<span data-ttu-id="9c704-108">Если были включены современных проверки подлинности в Скайп для бизнеса в Интернет или локальной, и/или Exchange Online или локальной и найдено необходимо отключить НЕГО, эти действия будут автоматически.</span><span class="sxs-lookup"><span data-stu-id="9c704-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c704-109">В статье «[Скайп для бизнеса топологии, поддерживаемые с проверкой подлинности на современном](https://technet.microsoft.com/en-us/library/mt803262.aspx)» во время Скайп для бизнеса в Интернет или локальной, у НЕГО mixed топологии и обратите внимание на поддерживаемые топологии, прежде чем приступить к работе.</span><span class="sxs-lookup"><span data-stu-id="9c704-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="9c704-110">Как отключить современных проверки подлинности гибридной (Exchange)</span><span class="sxs-lookup"><span data-stu-id="9c704-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="9c704-111">**Локальную систему Exchange**: Откройте командную консоль Exchange и выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="9c704-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="9c704-p103">**Exchange Online**: [подключение к Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) с помощью удаленной оболочки PowerShell. Выполните следующую команду, чтобы включить флага *OAuth2ClientProfileEnabled* значение «false».</span><span class="sxs-lookup"><span data-stu-id="9c704-p103">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="9c704-114">Как отключить современных проверки подлинности гибридной (Скайп для бизнеса)</span><span class="sxs-lookup"><span data-stu-id="9c704-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="9c704-115">**Скайп для бизнеса в локальной**: выполните следующие команды в Скайп оболочки управления бизнеса:</span><span class="sxs-lookup"><span data-stu-id="9c704-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="9c704-p104">**Скайп для бизнеса в Интернете**: [подключение к Скайп для бизнеса через Интернет](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) с помощью удаленной оболочки PowerShell. Выполните следующую команду, чтобы отключить современных проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="9c704-p104">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell. Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="9c704-118">[Ссылку на обзор современного проверки подлинности](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="9c704-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

