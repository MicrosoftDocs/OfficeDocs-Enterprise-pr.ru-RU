---
title: Отключение синхронизации каталогов для Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Узнайте, как использовать PowerShell для отключения синхронизации службы каталогов для Office 365
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542539"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="d3be2-103">Отключение синхронизации каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="d3be2-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="d3be2-p101">PowerShell можно использовать для отключения синхронизации службы каталогов. Отключение синхронизации службы каталогов для устранения неполадок не рекомендуется. Если вам требуется помощь в устранении неполадок синхронизации службы каталогов, в статье [устранению проблем с синхронизацией каталогов для Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="d3be2-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="d3be2-107">[Обратитесь в службу поддержки](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) продуктов business при необходимости.</span><span class="sxs-lookup"><span data-stu-id="d3be2-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="d3be2-108">Отключение синхронизации службы каталогов</span><span class="sxs-lookup"><span data-stu-id="d3be2-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="d3be2-109">Для отключения синхронизации службы каталогов:</span><span class="sxs-lookup"><span data-stu-id="d3be2-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="d3be2-p102">Во-первых Установка необходимого программного обеспечения и подключитесь к своей подписке Office 365. Инструкции для них в разделе [подключение к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="d3be2-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="d3be2-112">Использование [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) для отключения синхронизации службы каталогов:</span><span class="sxs-lookup"><span data-stu-id="d3be2-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```