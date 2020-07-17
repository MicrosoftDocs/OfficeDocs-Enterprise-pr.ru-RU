---
title: Отключение синхронизации каталогов для Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Узнайте, как отключить синхронизацию службы каталогов для Microsoft 365 с помощью PowerShell.
ms.openlocfilehash: 935d7e26c7b99aba876500e6b9d428557aed5b9c
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906212"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="df6eb-103">Отключение синхронизации каталогов для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="df6eb-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="df6eb-104">Вы можете отключить синхронизацию службы каталогов с помощью PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df6eb-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="df6eb-105">Тем не менее, не рекомендуется отключать синхронизацию службы каталогов в качестве действия по устранению неполадок.</span><span class="sxs-lookup"><span data-stu-id="df6eb-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="df6eb-106">Если вам нужна помощь с устранением проблем с синхронизацией службы каталогов, обратитесь к разделу [Устранение проблем с синхронизацией каталогов для статьи Microsoft 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="df6eb-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="df6eb-107">При необходимости [свяжитесь со службой поддержки](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) для бизнес-продуктов.</span><span class="sxs-lookup"><span data-stu-id="df6eb-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="df6eb-108">Отключение синхронизации каталогов</span><span class="sxs-lookup"><span data-stu-id="df6eb-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="df6eb-109">Чтобы отключить синхронизацию службы каталогов, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="df6eb-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="df6eb-110">Сначала установите необходимое программное обеспечение и подключитесь к вашей подписке на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="df6eb-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="df6eb-111">Для получения инструкций обратитесь [к разделу Подключение к модулю Microsoft Azure Active Directory для Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="df6eb-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="df6eb-112">Используйте [Set – мсолдирсинценаблед](https://go.microsoft.com/fwlink/p/?LinkId=821939) , чтобы отключить синхронизацию службы каталогов:</span><span class="sxs-lookup"><span data-stu-id="df6eb-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
