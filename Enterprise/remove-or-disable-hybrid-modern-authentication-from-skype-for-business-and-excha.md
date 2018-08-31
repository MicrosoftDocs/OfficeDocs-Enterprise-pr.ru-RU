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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Удаление гибридной современной проверки подлинности из Skype для бизнеса и Exchange или ее отключение

При включении гибридного современных проверки подлинности (НЕГО) обнаружить, что она не подходит для текущей среды можно отключить НЕГО. В этой статье объясняется, как.
  
## <a name="who-is-this-article-for"></a>Для кого предназначена эта статья?

Если были включены современных проверки подлинности в Скайп для бизнеса в Интернет или локальной, и/или Exchange Online или локальной и найдено необходимо отключить НЕГО, эти действия будут автоматически.
  
 **Важные** В статье « [Скайп для бизнеса топологии, поддерживаемые с проверкой подлинности на современном](https://technet.microsoft.com/en-us/library/mt803262.aspx)» во время Скайп для бизнеса в Интернет или локальной, у НЕГО mixed топологии и обратите внимание на поддерживаемые топологии, прежде чем приступить к работе.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Как отключить современных проверки подлинности гибридной (Exchange)

1. **Локальную систему Exchange**: Откройте командную консоль Exchange и выполните следующую команду. 
    
1. SET-OrganizationConfig-OAuth2ClientProfileEnabled $false
    
2. SET-AuthServer-Identity evoSTS - IsDefaultAuthorizationEndpoint $false
    
2. **Exchange Online**: подключение к Exchange Online с помощью удаленной оболочки PowerShell. Выполните следующую команду, чтобы включить флага *OAuth2ClientProfileEnabled* значение «false». 
    
1. SET-OrganizationConfig-OAuth2ClientProfileEnabled: $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Как отключить современных проверки подлинности гибридной (Скайп для бизнеса)

1. **Скайп для бизнеса в локальной**: выполните следующие команды в Скайп оболочки управления бизнеса.
    
1. SET-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity «»
    
2. **Скайп для бизнеса в Интернете**: подключение к Скайп для бизнеса через Интернет с помощью удаленной оболочки PowerShell. Выполните следующую команду для отключения современных проверки подлинности. 
    
1. SET-CsOAuthConfiguration - ClientAdalAuthOverride не разрешены
    
[Ссылку на обзор современного проверки подлинности](hybrid-modern-auth-overview.md) . 
  

