---
title: Отключение синхронизации службы каталогов для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Узнайте, как отключить синхронизацию службы каталогов для Office 365 с помощью PowerShell.
ms.openlocfilehash: 83a01d827217db141016f622a2cb417f93f88e76
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070365"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="69225-103">Отключение синхронизации службы каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="69225-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="69225-104">Вы можете отключить синхронизацию службы каталогов с помощью PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69225-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="69225-105">Тем не менее, не рекомендуется отключать синхронизацию службы каталогов в качестве действия по устранению неполадок.</span><span class="sxs-lookup"><span data-stu-id="69225-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="69225-106">Если вам нужна помощь с устранением проблем с синхронизацией службы каталогов, обратитесь к разделу [Устранение проблем с синхронизацией каталогов для Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="69225-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="69225-107">При необходимости [свяжитесь со службой поддержки](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) для бизнес-продуктов.</span><span class="sxs-lookup"><span data-stu-id="69225-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="69225-108">Отключение синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="69225-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="69225-109">Чтобы отключить синхронизацию службы каталогов, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="69225-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="69225-110">Сначала установите необходимое программное обеспечение и подключитесь к вашей подписке на Office 365.</span><span class="sxs-lookup"><span data-stu-id="69225-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="69225-111">Инструкции для обоих [способов приведены в статье подключение к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="69225-111">For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="69225-112">Используйте [Set – мсолдирсинценаблед](https://go.microsoft.com/fwlink/p/?LinkId=821939) , чтобы отключить синхронизацию службы каталогов:</span><span class="sxs-lookup"><span data-stu-id="69225-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```