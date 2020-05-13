---
title: Управление Microsoft Teams с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Сводка: использование PowerShell в Office 365 для управления Microsoft Teams.'
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209129"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a>Управление Microsoft Teams с помощью PowerShell для Office 365

Вы можете управлять Microsoft Teams с помощью PowerShell для Office 365.
  
Сначала установите [модуль Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).
    
## <a name="sign-in-with-a-user-name-and-password"></a>Вход с использованием имени пользователя и пароля

Для Office 365 для международных (+ GCC) облаков:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

Для облака Office 365 для государственных учреждений (США): 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

Для Office 365 U.S. правительством GCC High Cloud:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>Вход с многофакторной проверкой подлинности (MFA)

Для Office 365 для международных (+ GCC) облаков:

```powershell
Connect-MicrosoftTeams
```

Для облака Office 365 для государственных учреждений (США): 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

Для Office 365 U.S. правительством GCC High Cloud:

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>Отключение от Microsoft Teams

Используйте эту команду:

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>См. также

[Общие сведения о Teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

