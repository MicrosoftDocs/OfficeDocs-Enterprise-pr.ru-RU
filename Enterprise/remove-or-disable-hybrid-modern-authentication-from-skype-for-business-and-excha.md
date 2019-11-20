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
ms.openlocfilehash: 72b902db04fd7c56d573d9df079f353a3f6cdc4f
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748397"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="b4bb6-104">Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение</span><span class="sxs-lookup"><span data-stu-id="b4bb6-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="b4bb6-105">*Эта статья относится как к Office 365 Enterprise, так и к Microsoft 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="b4bb6-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="b4bb6-106">Если Гибридная современная проверка подлинности (HMA) включена только для того, чтобы найти непригодную для текущей среды, можно отключить HMA.</span><span class="sxs-lookup"><span data-stu-id="b4bb6-106">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="b4bb6-107">В этой статье описывается, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="b4bb6-107">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="b4bb6-108">Для кого предназначена эта статья?</span><span class="sxs-lookup"><span data-stu-id="b4bb6-108">Who is this article for?</span></span>

<span data-ttu-id="b4bb6-109">Если вы включили современные проверки подлинности в Skype для бизнеса Online или локальной среде, а также на сервере Exchange Online или в локальной среде, и вам нужно отключить сегмент HMA, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b4bb6-109">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4bb6-110">Ознакомьтесь со статьей "[топологии Skype для бизнеса, поддерживаемые с современной проверкой подлинности](https://technet.microsoft.com/library/mt803262.aspx)", если вы находитесь в Skype для бизнеса Online или в локальной среде, у вас есть смешанная топология HMA, и вам нужно взглянуть на поддерживаемые топологии перед началом работы.</span><span class="sxs-lookup"><span data-stu-id="b4bb6-110">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="b4bb6-111">Как отключить гибридную современные проверки подлинности (Exchange)</span><span class="sxs-lookup"><span data-stu-id="b4bb6-111">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="b4bb6-112">**Локальная служба Exchange**: Откройте командную консоль Exchange и выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="b4bb6-112">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="b4bb6-113">**Exchange Online**: [Подключение к Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) с помощью удаленного сеанса PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4bb6-113">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="b4bb6-114">Выполните следующую команду, чтобы превратить флаг *OAuth2ClientProfileEnabled* в значение false:</span><span class="sxs-lookup"><span data-stu-id="b4bb6-114">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="b4bb6-115">Как отключить гибридную современные проверки подлинности (Skype для бизнеса)</span><span class="sxs-lookup"><span data-stu-id="b4bb6-115">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="b4bb6-116">**Локальная среда Skype для бизнеса**: выполните следующие команды в командной консоли Skype для бизнеса:</span><span class="sxs-lookup"><span data-stu-id="b4bb6-116">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="b4bb6-117">**Skype для бизнеса Online**: [Подключение к Skype для бизнеса Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) с помощью удаленного сеанса PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4bb6-117">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="b4bb6-118">Выполните следующую команду, чтобы отключить современные проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="b4bb6-118">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="b4bb6-119">[Выполните обратное соединение с обзором современной проверки подлинности](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="b4bb6-119">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

