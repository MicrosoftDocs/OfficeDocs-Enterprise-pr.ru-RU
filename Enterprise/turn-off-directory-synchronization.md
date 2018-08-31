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
# <a name="turn-off-directory-synchronization-for-office-365"></a>Отключение синхронизации каталогов для Office 365
PowerShell можно использовать для отключения синхронизации службы каталогов. Отключение синхронизации службы каталогов для устранения неполадок не рекомендуется. Если вам требуется помощь в устранении неполадок синхронизации службы каталогов, в статье [устранению проблем с синхронизацией каталогов для Office 365](fix-problems-with-directory-synchronization.md) . 
  
[Обратитесь в службу поддержки](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) продуктов business при необходимости.
  
## <a name="turn-off-directory-synchronization"></a>Отключение синхронизации службы каталогов  
Для отключения синхронизации службы каталогов:
  
1. Во-первых Установка необходимого программного обеспечения и подключитесь к своей подписке Office 365. Инструкции для них в разделе [подключение к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Использование [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) для отключения синхронизации службы каталогов: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```