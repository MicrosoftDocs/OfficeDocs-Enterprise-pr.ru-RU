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
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="f782b-103">Управление Microsoft Teams с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="f782b-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="f782b-104">Вы можете управлять Microsoft Teams с помощью PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="f782b-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="f782b-105">Сначала установите [модуль Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="f782b-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="f782b-106">Вход с использованием имени пользователя и пароля</span><span class="sxs-lookup"><span data-stu-id="f782b-106">Sign in with a user name and password</span></span>

<span data-ttu-id="f782b-107">Для Office 365 для международных (+ GCC) облаков:</span><span class="sxs-lookup"><span data-stu-id="f782b-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="f782b-108">Для облака Office 365 для государственных учреждений (США):</span><span class="sxs-lookup"><span data-stu-id="f782b-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="f782b-109">Для Office 365 U.S. правительством GCC High Cloud:</span><span class="sxs-lookup"><span data-stu-id="f782b-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="f782b-110">Вход с многофакторной проверкой подлинности (MFA)</span><span class="sxs-lookup"><span data-stu-id="f782b-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="f782b-111">Для Office 365 для международных (+ GCC) облаков:</span><span class="sxs-lookup"><span data-stu-id="f782b-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="f782b-112">Для облака Office 365 для государственных учреждений (США):</span><span class="sxs-lookup"><span data-stu-id="f782b-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="f782b-113">Для Office 365 U.S. правительством GCC High Cloud:</span><span class="sxs-lookup"><span data-stu-id="f782b-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="f782b-114">Отключение от Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f782b-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="f782b-115">Используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="f782b-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="f782b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="f782b-116">See also</span></span>

[<span data-ttu-id="f782b-117">Общие сведения о Teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="f782b-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="f782b-118">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="f782b-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f782b-119">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f782b-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

