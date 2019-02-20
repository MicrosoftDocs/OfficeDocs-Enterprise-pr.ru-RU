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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Узнайте, как отключить синхронизацию службы каталогов для Office 365 с помощью PowerShell.
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085078"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Отключение синхронизации каталогов для Office 365
Вы можете отключить синхронизацию службы каталогов с помощью PowerShell. Тем не менее, не рекомендуется отключать синхронизацию службы каталогов в качестве действия по устранению неполадок. Если вам нужна помощь с устранением проблем с синхронизацией службы каталогов, обратитесь к разделу [Устранение проблем с синхронизацией каталогов для Office 365](fix-problems-with-directory-synchronization.md) . 
  
При необходимости [свяжитесь со службой поддержки](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) для бизнес-продуктов.
  
## <a name="turn-off-directory-synchronization"></a>Отключение синхронизации службы каталогов  
Чтобы отключить синхронизацию службы каталогов, выполните указанные ниже действия.
  
1. Сначала установите необходимое программное обеспечение и подключитесь к вашей подписке на Office 365. Инструкции для обоих [способов приведены в статье подключение к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Используйте [Set – мсолдирсинценаблед](https://go.microsoft.com/fwlink/p/?LinkId=821939) , чтобы отключить синхронизацию службы каталогов: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```