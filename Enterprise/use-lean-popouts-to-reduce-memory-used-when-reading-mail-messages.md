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
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="eb4db-103">Используйте экономичных popouts, чтобы уменьшить объем памяти, используемый при чтении сообщения почты</span><span class="sxs-lookup"><span data-stu-id="eb4db-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="eb4db-p101">В этой статье содержатся сведения о повышении производительности загрузки сообщений в Outlook в Интернете. В этой статье является частью проекта [сети планирование и настройка производительности для Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="eb4db-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="eb4db-p102">Как глобальный администратор Office 365 можно настроить Outlook в Интернете для предоставления *экономичных popouts* , меньшего размера, меньше большого объема памяти версии определенных сообщений электронной почты в Microsoft пограничный сервер или Internet Explorer. При настройке экономичных popouts для Outlook в Интернете к просмотру компоненты на стороне сервера загружаются, оптимизировать производительность.</span><span class="sxs-lookup"><span data-stu-id="eb4db-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="eb4db-108">По состоянию на март 2018 экономичных popouts, в настоящее время недоступны для сообщений, которые задают ограничения прав использования, таких как управление правами на доступ к данным (IRM).</span><span class="sxs-lookup"><span data-stu-id="eb4db-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="eb4db-109">Эти компоненты будут работать в главном окне, но не доступны в экономичных popouts:</span><span class="sxs-lookup"><span data-stu-id="eb4db-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="eb4db-110">Надстройки Outlook</span><span class="sxs-lookup"><span data-stu-id="eb4db-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="eb4db-111">Скайп для бизнеса сведений о присутствии</span><span class="sxs-lookup"><span data-stu-id="eb4db-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="eb4db-112">**Чтобы настроить экономичных popouts для всех пользователей в организации Office 365**</span><span class="sxs-lookup"><span data-stu-id="eb4db-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="eb4db-113">[Подключение к Exchange Online с помощью удаленной оболочки PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="eb4db-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="eb4db-114">Используйте командлет [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) с параметром LeanPopoutEnabled следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eb4db-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="eb4db-115">Например, чтобы включить экономичных popouts для всех пользователей в вашей организации:</span><span class="sxs-lookup"><span data-stu-id="eb4db-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="eb4db-116">Чтобы отключить экономичных popouts для всех пользователей в вашей организации:</span><span class="sxs-lookup"><span data-stu-id="eb4db-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


