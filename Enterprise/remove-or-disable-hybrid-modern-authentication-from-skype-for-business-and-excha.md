---
title: Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: Если Гибридная современная проверка подлинности (HMA) включена только для того, чтобы найти непригодную для текущей среды, можно отключить HMA. В этой статье описывается, как это сделать.
ms.openlocfilehash: 9f1236775f60fdb37ab12cd7cfb7eabd9763466d
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031604"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="225fb-104">Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение</span><span class="sxs-lookup"><span data-stu-id="225fb-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="225fb-105">Если Гибридная современная проверка подлинности (HMA) включена только для того, чтобы найти непригодную для текущей среды, можно отключить HMA.</span><span class="sxs-lookup"><span data-stu-id="225fb-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="225fb-106">В этой статье описывается, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="225fb-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="225fb-107">Для кого предназначена эта статья?</span><span class="sxs-lookup"><span data-stu-id="225fb-107">Who is this article for?</span></span>

<span data-ttu-id="225fb-108">Если вы включили современные проверки подлинности в Skype для бизнеса Online или локальной среде, а также на сервере Exchange Online или в локальной среде, и вам нужно отключить сегмент HMA, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="225fb-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="225fb-109">Ознакомьтесь со статьей "[топологии Skype для бизнеса, поддерживаемые с современной проверкой подлинности](https://technet.microsoft.com/library/mt803262.aspx)", если вы находитесь в Skype для бизнеса Online или в локальной среде, у вас есть смешанная топология HMA, и вам нужно взглянуть на поддерживаемые топологии перед началом работы.</span><span class="sxs-lookup"><span data-stu-id="225fb-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="225fb-110">Как отключить гибридную современные проверки подлинности (Exchange)</span><span class="sxs-lookup"><span data-stu-id="225fb-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="225fb-111">**Локальная служба Exchange**: Откройте командную консоль Exchange и выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="225fb-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="225fb-112">**Exchange Online**: [Подключение к Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) с помощью удаленного сеанса PowerShell.</span><span class="sxs-lookup"><span data-stu-id="225fb-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="225fb-113">Выполните следующую команду, чтобы превратить флаг *OAuth2ClientProfileEnabled* в значение false:</span><span class="sxs-lookup"><span data-stu-id="225fb-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="225fb-114">Как отключить гибридную современные проверки подлинности (Skype для бизнеса)</span><span class="sxs-lookup"><span data-stu-id="225fb-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="225fb-115">**Локальная среда Skype для бизнеса**: выполните следующие команды в командной консоли Skype для бизнеса:</span><span class="sxs-lookup"><span data-stu-id="225fb-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="225fb-116">**Skype для бизнеса Online**: [Подключение к Skype для бизнеса Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) с помощью удаленного сеанса PowerShell.</span><span class="sxs-lookup"><span data-stu-id="225fb-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="225fb-117">Выполните следующую команду, чтобы отключить современные проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="225fb-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="225fb-118">[Выполните обратное соединение с обзором современной проверки подлинности](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="225fb-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

