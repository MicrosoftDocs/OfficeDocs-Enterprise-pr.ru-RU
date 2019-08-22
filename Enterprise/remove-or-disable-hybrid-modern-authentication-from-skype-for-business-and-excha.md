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
ms.openlocfilehash: 91373adf590ad9a69880de20897795ced23d98b8
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493326"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение

Если Гибридная современная проверка подлинности (HMA) включена только для того, чтобы найти непригодную для текущей среды, можно отключить HMA. В этой статье описывается, как это сделать.
  
## <a name="who-is-this-article-for"></a>Для кого предназначена эта статья?

Если вы включили современные проверки подлинности в Skype для бизнеса Online или локальной среде, а также на сервере Exchange Online или в локальной среде, и вам нужно отключить сегмент HMA, выполните указанные ниже действия.

> [!IMPORTANT]
> Ознакомьтесь со статьей "[топологии Skype для бизнеса, поддерживаемые с современной проверкой](https://technet.microsoft.com/en-us/library/mt803262.aspx)подлинности", если вы находитесь в Skype для бизнеса Online или в локальной среде, у вас есть смешанная топология HMA, и вам нужно взглянуть на поддерживаемые топологии перед началом работы.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Как отключить гибридную современные проверки подлинности (Exchange)

1. **Локальная служба Exchange**: Откройте командную консоль Exchange и выполните следующие команды: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Подключение к Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) с помощью удаленного сеанса PowerShell. Выполните следующую команду, чтобы превратить флаг *OAuth2ClientProfileEnabled* в значение false:

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Как отключить гибридную современные проверки подлинности (Skype для бизнеса)

1. **Локальная среда Skype для бизнеса**: выполните следующие команды в командной консоли Skype для бизнеса:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype для бизнеса Online**: [Подключение к Skype для бизнеса Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) с помощью удаленного сеанса PowerShell. Выполните следующую команду, чтобы отключить современные проверки подлинности:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Выполните обратное соединение с обзором современной проверки](hybrid-modern-auth-overview.md) подлинности. 
  

