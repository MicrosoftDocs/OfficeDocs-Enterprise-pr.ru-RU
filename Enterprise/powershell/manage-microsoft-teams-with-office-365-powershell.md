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
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429214"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="0b4a9-103">Управление Microsoft Teams с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b4a9-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="0b4a9-104">*Эта статья относится к Microsoft 365 корпоративный и Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="0b4a9-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="0b4a9-105">Вы можете управлять Microsoft Teams с помощью PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b4a9-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="0b4a9-106">Сначала установите [модуль Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="0b4a9-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="0b4a9-107">Вход с использованием имени пользователя и пароля</span><span class="sxs-lookup"><span data-stu-id="0b4a9-107">Sign in with a user name and password</span></span>

<span data-ttu-id="0b4a9-108">Для Office 365 для международных (+ GCC) облаков:</span><span class="sxs-lookup"><span data-stu-id="0b4a9-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="0b4a9-109">Для облака Office 365 для государственных учреждений (США):</span><span class="sxs-lookup"><span data-stu-id="0b4a9-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="0b4a9-110">Для Office 365 U.S. правительством GCC High Cloud:</span><span class="sxs-lookup"><span data-stu-id="0b4a9-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="0b4a9-111">Вход с многофакторной проверкой подлинности (MFA)</span><span class="sxs-lookup"><span data-stu-id="0b4a9-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="0b4a9-112">Для Office 365 для международных (+ GCC) облаков:</span><span class="sxs-lookup"><span data-stu-id="0b4a9-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="0b4a9-113">Для облака Office 365 для государственных учреждений (США):</span><span class="sxs-lookup"><span data-stu-id="0b4a9-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="0b4a9-114">Для Office 365 U.S. правительством GCC High Cloud:</span><span class="sxs-lookup"><span data-stu-id="0b4a9-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="0b4a9-115">Отключение от Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0b4a9-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="0b4a9-116">Используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="0b4a9-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="0b4a9-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0b4a9-117">See also</span></span>

[<span data-ttu-id="0b4a9-118">Общие сведения о Teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b4a9-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="0b4a9-119">Управление Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b4a9-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0b4a9-120">Начало работы с PowerShell для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0b4a9-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

