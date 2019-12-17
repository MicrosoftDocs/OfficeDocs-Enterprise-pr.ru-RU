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
ms.openlocfilehash: de7cfcbc11ed281e412c68674b808613b3421041
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072401"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Отключение синхронизации службы каталогов для Office 365
Вы можете отключить синхронизацию службы каталогов с помощью PowerShell. Тем не менее, не рекомендуется отключать синхронизацию службы каталогов в качестве действия по устранению неполадок. Если вам нужна помощь с устранением проблем с синхронизацией службы каталогов, обратитесь к разделу [Устранение проблем с синхронизацией каталогов для Office 365](fix-problems-with-directory-synchronization.md) . 
  
При необходимости [свяжитесь со службой поддержки](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) для бизнес-продуктов.
  
## <a name="turn-off-directory-synchronization"></a>Отключение синхронизации каталогов  
Чтобы отключить синхронизацию службы каталогов, выполните указанные ниже действия.
  
1. Сначала установите необходимое программное обеспечение и подключитесь к вашей подписке на Office 365. Инструкции для обоих [способов приведены в статье подключение к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Используйте [Set – мсолдирсинценаблед](https://go.microsoft.com/fwlink/p/?LinkId=821939) , чтобы отключить синхронизацию службы каталогов: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```