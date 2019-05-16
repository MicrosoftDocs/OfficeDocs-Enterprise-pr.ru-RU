---
title: Настройка производительности Exchange Online
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: В этой статье представлены общие советы и ссылки на другие ресурсы, содержащие сведения о том, как увеличить производительность Exchange Online.
ms.openlocfilehash: d736568687da5ffe0ebed5a57a6afa6f93173c54
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070355"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="73153-103">Настройка производительности Exchange Online</span><span class="sxs-lookup"><span data-stu-id="73153-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="73153-104">В этой статье представлены общие советы и ссылки на другие ресурсы, содержащие сведения о том, как увеличить производительность Exchange Online, особенно перед переносом.</span><span class="sxs-lookup"><span data-stu-id="73153-104">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online, particularly in front of a migration.</span></span> <span data-ttu-id="73153-105">Эта статья является частью [планирования сети и настройки производительности для проекта Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="73153-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="73153-106">Факторы, которые необходимо учитывать для улучшения производительности Exchange Online</span><span class="sxs-lookup"><span data-stu-id="73153-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="73153-107">Чтобы повысить скорость миграции и снизить ограничения пропускной способности Организации для Exchange Online, учитывайте следующее:</span><span class="sxs-lookup"><span data-stu-id="73153-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="73153-108">**Уменьшите размеры почтового ящика.**</span><span class="sxs-lookup"><span data-stu-id="73153-108">**Reduce mailbox sizes.**</span></span> <span data-ttu-id="73153-109">Уменьшение размера почтового ящика повышает скорость миграции.</span><span class="sxs-lookup"><span data-stu-id="73153-109">Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="73153-110">**Используйте возможности перемещения почтовых ящиков в гибридном развертывании Exchange.**</span><span class="sxs-lookup"><span data-stu-id="73153-110">**Use the mailbox move capabilities with an Exchange hybrid deployment.**</span></span> <span data-ttu-id="73153-111">В гибридном развертывании Exchange — автономная почта (в виде. Для OST-файлов) не требуется повторный загрузку при переходе на Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="73153-111">With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online.</span></span> <span data-ttu-id="73153-112">Это значительно сокращает требования к пропускной способности при загрузке.</span><span class="sxs-lookup"><span data-stu-id="73153-112">This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="73153-113">**Запланируйте перемещение почтовых ящиков в периоды с небольшим трафиком из Интернета и нехваткой локального использования Exchange.**</span><span class="sxs-lookup"><span data-stu-id="73153-113">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.**</span></span> <span data-ttu-id="73153-114">При перепланировании запросы на миграцию отправляются на прокси-сервер репликации почтовых ящиков и могут не выполняться немедленно.</span><span class="sxs-lookup"><span data-stu-id="73153-114">When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="73153-115">**Используйте экономичный всплывающих окон для Outlook в Интернете.**</span><span class="sxs-lookup"><span data-stu-id="73153-115">**Use lean popouts for Outlook on the web.**</span></span> <span data-ttu-id="73153-116">Экономичный всплывающих окон предоставляет более мелкие и менее ресурсоемкие версии определенных сообщений электронной почты в Microsoft EDGE или Internet Explorer, выполнив отображение некоторых компонентов на сервере.</span><span class="sxs-lookup"><span data-stu-id="73153-116">Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server.</span></span> <span data-ttu-id="73153-117">Более подробную информацию [можно узнать в статье использование экономичных всплывающих окон для уменьшения объема памяти, используемой при чтении почтовых сообщений](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="73153-117">For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>


## <a name="general-advice"></a><span data-ttu-id="73153-118">Общие рекомендации</span><span class="sxs-lookup"><span data-stu-id="73153-118">General advice</span></span>

- <span data-ttu-id="73153-119">Убедитесь, что при поиске в DNS для outlook.office.com в центре обработки данных в логической папке находится центр обработки данных.</span><span class="sxs-lookup"><span data-stu-id="73153-119">Make certain that DNS lookup for outlook.office.com enters the MS-datacenter at a logical entry location for your location.</span></span>

- <span data-ttu-id="73153-120">Проанализируйте кэширование почтовых ящиков и выберите соответствующие параметры (Re.</span><span class="sxs-lookup"><span data-stu-id="73153-120">Research mailbox caching and choose the appropriate options (re.</span></span> <span data-ttu-id="73153-121">период кэширования, кэширование общих почтовых ящиков, et Цетера).</span><span class="sxs-lookup"><span data-stu-id="73153-121">caching period, shared mailbox caching, et cetera).</span></span>

- <span data-ttu-id="73153-122">Отследите, чтобы данные Outlook переходили через VPN-подключения (в Центральный офис) перед переходом по Интернету.</span><span class="sxs-lookup"><span data-stu-id="73153-122">Keep your Outlook data from passing over VPN connections (to a central office) before it goes over the Internet.</span></span>

- <span data-ttu-id="73153-123">Убедитесь, что данные почтового ящика соответствуют ограничениям для папки и элемента, а также сумм.</span><span class="sxs-lookup"><span data-stu-id="73153-123">Be sure your mailbox data adheres to the limitations on folder, and item, amounts.</span></span>
    
<span data-ttu-id="73153-124">Более подробную информацию о производительности миграции Exchange вы найдете в статье [Office 365 Migration Performance and Best Practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="73153-124">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

