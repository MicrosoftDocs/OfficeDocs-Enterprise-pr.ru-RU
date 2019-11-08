---
title: Использование экономичных всплывающих окон для уменьшения объема памяти, используемой при чтении почтовых сообщений
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: В этой статье содержатся сведения о том, как улучшить производительность загрузки сообщений в Outlook в Интернете.
ms.openlocfilehash: bb9a11a27af0b66f1dd557c459d1904c2e57ae92
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030874"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Использование экономичных всплывающих окон для уменьшения объема памяти, используемой при чтении почтовых сообщений

В этой статье содержатся сведения о том, как улучшить производительность загрузки сообщений в Outlook в Интернете. Эта статья является частью [планирования сети и настройки производительности для проекта Office 365](https://aka.ms/tune) .
   
Как глобальный администратор Office 365 вы можете настроить Outlook в Интернете, чтобы обеспечить *экономичное всплывающих окон* , меньшее количество сообщений электронной почты в Microsoft EDGE или Internet Explorer. Когда экономичный всплывающих окон настраивается для Outlook в Интернете, загружаются серверные компоненты, которые оптимизируют производительность. 
  
> [!NOTE]
> На 2018 марта в настоящее время экономичный всплывающих окон в настоящее время недоступен для сообщений, в которых указаны ограничения прав на использование, например, управления правами на доступ к данным (IRM). 
  
Эти функции продолжат работу в главном окне, но недоступны в экономичных всплывающих окон:
  
- Надстройки Outlook
    
- Присутствие в Skype для бизнеса
    
 **Настройка экономичного всплывающих окон для всех пользователей в организации Office 365**
  
1. [Подключитесь к Exchange Online с помощью удаленной оболочки PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Выполните командлет [Set – OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) с параметром леанпопаутенаблед следующим образом: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Например, чтобы включить экономичный всплывающих окон для всех пользователей в Организации:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Чтобы отключить экономичный всплывающих окон для всех пользователей в Организации:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


