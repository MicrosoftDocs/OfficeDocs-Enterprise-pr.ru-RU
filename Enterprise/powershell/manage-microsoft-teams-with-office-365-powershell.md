---
title: Управление Microsoft Teams с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Сводка: использование PowerShell для управления Microsoft Teams.'
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230615"
---
# <a name="manage-microsoft-teams-with-powershell"></a>Управление Microsoft Teams с помощью PowerShell

*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*

Вы можете управлять Microsoft Teams с помощью PowerShell.
  
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
  
[Управление Microsoft 365 с помощью PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с PowerShell для Microsoft 365](getting-started-with-office-365-powershell.md)

