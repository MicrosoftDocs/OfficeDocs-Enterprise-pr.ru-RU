---
title: Используйте экономичных popouts, чтобы уменьшить объем памяти, используемый при чтении сообщения почты
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: В этой статье содержатся сведения о повышении производительности загрузки сообщений в Outlook в Интернете.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542381"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Используйте экономичных popouts, чтобы уменьшить объем памяти, используемый при чтении сообщения почты

В этой статье содержатся сведения о повышении производительности загрузки сообщений в Outlook в Интернете. В этой статье является частью проекта [сети планирование и настройка производительности для Office 365](https://aka.ms/tune) .
   
Как глобальный администратор Office 365 можно настроить Outlook в Интернете для предоставления *экономичных popouts* , меньшего размера, меньше большого объема памяти версии определенных сообщений электронной почты в Microsoft пограничный сервер или Internet Explorer. При настройке экономичных popouts для Outlook в Интернете к просмотру компоненты на стороне сервера загружаются, оптимизировать производительность. 
  
> [!NOTE]
> По состоянию на март 2018 экономичных popouts, в настоящее время недоступны для сообщений, которые задают ограничения прав использования, таких как управление правами на доступ к данным (IRM). 
  
Эти компоненты будут работать в главном окне, но не доступны в экономичных popouts:
  
- Надстройки Outlook
    
- Скайп для бизнеса сведений о присутствии
    
 **Чтобы настроить экономичных popouts для всех пользователей в организации Office 365**
  
1. [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Используйте командлет [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) с параметром LeanPopoutEnabled следующим образом: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    Например, чтобы включить экономичных popouts для всех пользователей в вашей организации:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    Чтобы отключить экономичных popouts для всех пользователей в вашей организации:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


