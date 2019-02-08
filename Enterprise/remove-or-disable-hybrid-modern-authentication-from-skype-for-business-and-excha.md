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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение

При включении гибридного современных проверки подлинности (НЕГО) обнаружить, что она не подходит для текущей среды можно отключить НЕГО. В этой статье объясняется, как.
  
## <a name="who-is-this-article-for"></a>Для кого предназначена эта статья?

Если были включены современных проверки подлинности в Скайп для бизнеса в Интернет или локальной, и/или Exchange Online или локальной и найдено необходимо отключить НЕГО, эти действия будут автоматически.

> [!IMPORTANT]
> В статье «[Скайп для бизнеса топологии, поддерживаемые с проверкой подлинности на современном](https://technet.microsoft.com/en-us/library/mt803262.aspx)» во время Скайп для бизнеса в Интернет или локальной, у НЕГО mixed топологии и обратите внимание на поддерживаемые топологии, прежде чем приступить к работе.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Как отключить современных проверки подлинности гибридной (Exchange)

1. **Локальную систему Exchange**: Откройте командную консоль Exchange и выполните следующие команды: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [подключение к Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) с помощью удаленной оболочки PowerShell. Выполните следующую команду, чтобы включить флага *OAuth2ClientProfileEnabled* значение «false».

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Как отключить современных проверки подлинности гибридной (Скайп для бизнеса)

1. **Скайп для бизнеса в локальной**: выполните следующие команды в Скайп оболочки управления бизнеса:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Скайп для бизнеса в Интернете**: [подключение к Скайп для бизнеса через Интернет](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) с помощью удаленной оболочки PowerShell. Выполните следующую команду, чтобы отключить современных проверки подлинности:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Ссылку на обзор современного проверки подлинности](hybrid-modern-auth-overview.md) . 
  

