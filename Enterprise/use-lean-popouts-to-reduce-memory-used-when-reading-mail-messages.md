---
title: Использование экономичных всплывающих окон для уменьшения объема памяти, используемой при чтении почтовых сообщений
ms.author: krowley
author: kccross
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
ms.openlocfilehash: 344047363bd58850fcd08a7f8f2fd46de757668c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070565"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="f7db3-103">Использование экономичных всплывающих окон для уменьшения объема памяти, используемой при чтении почтовых сообщений</span><span class="sxs-lookup"><span data-stu-id="f7db3-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="f7db3-104">В этой статье содержатся сведения о том, как улучшить производительность загрузки сообщений в Outlook в Интернете.</span><span class="sxs-lookup"><span data-stu-id="f7db3-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="f7db3-105">Эта статья является частью [планирования сети и настройки производительности для проекта Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="f7db3-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="f7db3-106">Как глобальный администратор Office 365 вы можете настроить Outlook в Интернете, чтобы обеспечить экономичное *всплывающих окон* , меньшее количество сообщений электронной почты в Microsoft EDGE или Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f7db3-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="f7db3-107">Когда экономичный всплывающих окон настраивается для Outlook в Интернете, загружаются серверные компоненты, которые оптимизируют производительность.</span><span class="sxs-lookup"><span data-stu-id="f7db3-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="f7db3-108">На 2018 марта в настоящее время экономичный всплывающих окон в настоящее время недоступен для сообщений, в которых указаны ограничения прав на использование, например, управления правами на доступ к данным (IRM).</span><span class="sxs-lookup"><span data-stu-id="f7db3-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="f7db3-109">Эти функции продолжат работу в главном окне, но недоступны в экономичных всплывающих окон:</span><span class="sxs-lookup"><span data-stu-id="f7db3-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="f7db3-110">Надстройки Outlook</span><span class="sxs-lookup"><span data-stu-id="f7db3-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="f7db3-111">Присутствие в Skype для бизнеса</span><span class="sxs-lookup"><span data-stu-id="f7db3-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="f7db3-112">**Настройка экономичного всплывающих окон для всех пользователей в организации Office 365**</span><span class="sxs-lookup"><span data-stu-id="f7db3-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="f7db3-113">[Подключитесь к Exchange Online с помощью удаленной оболочки PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="f7db3-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="f7db3-114">Выполните командлет [Set – OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) с параметром леанпопаутенаблед следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f7db3-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="f7db3-115">Например, чтобы включить экономичный всплывающих окон для всех пользователей в Организации:</span><span class="sxs-lookup"><span data-stu-id="f7db3-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="f7db3-116">Чтобы отключить экономичный всплывающих окон для всех пользователей в Организации:</span><span class="sxs-lookup"><span data-stu-id="f7db3-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


