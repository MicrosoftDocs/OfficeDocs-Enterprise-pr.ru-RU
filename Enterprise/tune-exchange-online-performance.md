---
title: Настройка производительности Exchange Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: В этой статье содержатся общие рекомендации и ссылки на другие ресурсы, которые сообщают, как повысить производительность версией Exchange через Интернет.
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542671"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="6429f-103">Настройка производительности Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6429f-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="6429f-p101">В этой статье содержатся общие рекомендации и ссылки на другие ресурсы, которые сообщают, как повысить производительность версией Exchange через Интернет. В этой статье является частью проекта [сети планирование и настройка производительности для Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="6429f-p101">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="6429f-106">Важные факторы для повышения производительности Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6429f-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="6429f-107">Чтобы повысить скорость миграции и снизить ограничения пропускной способности вашей организации для Exchange Online, необходимо учитывайте следующее:</span><span class="sxs-lookup"><span data-stu-id="6429f-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="6429f-p102">**Сократите размеры почтовых ящиков.** Меньший размер почтового ящика повышает скорость миграции.</span><span class="sxs-lookup"><span data-stu-id="6429f-p102">**Reduce mailbox sizes.** Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="6429f-p103">**Используйте возможности перемещения почтового ящика с помощью гибридного развертывания Exchange.** В случае гибридного развертывания Exchange автономная почта (в виде OST-файлов) не требует повторной загрузки при миграции на Exchange Online. Это значительно снижает требования к пропускной способности для загрузки.</span><span class="sxs-lookup"><span data-stu-id="6429f-p103">**Use the mailbox move capabilities with an Exchange hybrid deployment.** With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online. This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="6429f-p104">**Составьте такое расписание, чтобы почтовые ящики перемещались в периоды низкого объема интернет-трафика и небольшой нагрузки на локальные системы Exchange.** При перемещении графика запросы на миграцию передаются на прокси-сервер репликации почтовых ящиков и не могут выполниться немедленно.</span><span class="sxs-lookup"><span data-stu-id="6429f-p104">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.** When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="6429f-p105">**Использовать экономичных popouts для Outlook в Интернете.** Экономичных popouts, предоставляют меньше большого объема памяти версии определенных сообщений электронной почты в Microsoft пограничный сервер или Internet Explorer с отображением некоторых компонентов на сервере. Дополнительные сведения можно [использовать экономичных popouts сократить объем памяти используется при чтении сообщений](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="6429f-p105">**Use lean popouts for Outlook on the web.** Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server. For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>
    
<span data-ttu-id="6429f-118">Дополнительные сведения о производительности миграции Exchange можно [производительности миграции Office 365 и рекомендации по обеспечению](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="6429f-118">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

