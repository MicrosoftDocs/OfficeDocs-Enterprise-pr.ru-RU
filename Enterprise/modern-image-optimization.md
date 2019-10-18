---
title: Оптимизация изображений на современных страницах сайтов SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Узнайте, как оптимизировать изображения на современных страницах сайтов SharePoint Online.
ms.openlocfilehash: 3884758dfb2f2a81a0a6ac10abcf51932abec666
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028236"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="de644-103">Оптимизация изображений на современных страницах сайтов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="de644-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="de644-104">С помощью этой статьи вы узнаете, как оптимизировать изображения на современных страницах сайтов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="de644-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="de644-105">Сведения об оптимизации изображений на классических сайтах публикации см. в статье [Оптимизация изображений для SharePoint Online](image-optimization-for-sharepoint-online.md).</span><span class="sxs-lookup"><span data-stu-id="de644-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="de644-106">Дополнительные сведения о производительности на современных порталах SharePoint Online см. в статье [Производительность в современном интерфейсе SharePoint](https://docs.microsoft.com/ru-RU/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="de644-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/ru-RU/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="de644-107">Использование средства диагностики страниц SharePoint для анализа оптимизации изображений</span><span class="sxs-lookup"><span data-stu-id="de644-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="de644-108">Средство **Диагностика страниц SharePoint** — это браузерное расширение для Chrome и [Microsoft Edge версии 77 или более поздней](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8), которое можно использовать для анализа современных и классических страниц сайтов публикации SharePoint.</span><span class="sxs-lookup"><span data-stu-id="de644-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="de644-109">Это средство предоставляет отчет о каждой проанализированной странице, показывающий, как страница работает в определенном наборе условий.</span><span class="sxs-lookup"><span data-stu-id="de644-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="de644-110">Чтобы установить и изучить средство диагностики страниц SharePoint, ознакомьтесь со статьей [Использование средства диагностики страниц SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="de644-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="de644-111">При анализе современного сайта SharePoint с помощью средства диагностики страниц SharePoint вы можете просматривать сведения о больших изображениях в панели _Диагностические тесты_.</span><span class="sxs-lookup"><span data-stu-id="de644-111">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="de644-112">Возможные результаты:</span><span class="sxs-lookup"><span data-stu-id="de644-112">Possible results include:</span></span>

- <span data-ttu-id="de644-113">**Внимание!** (красный цвет). Страница содержит **одно или несколько** изображений размером более 300 КБ</span><span class="sxs-lookup"><span data-stu-id="de644-113">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="de644-114">**Действия не требуются** (зеленый цвет). Страница не содержит изображений размером более 300 КБ</span><span class="sxs-lookup"><span data-stu-id="de644-114">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="de644-115">Если результат **Обнаружены большие изображения** отображается в разделе результатов **Внимание!**, вы можете щелкнуть его для просмотра дополнительных сведений.</span><span class="sxs-lookup"><span data-stu-id="de644-115">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![Результаты средства диагностики страниц](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="de644-117">Исправление проблем с большими изображениями</span><span class="sxs-lookup"><span data-stu-id="de644-117">Remediate large image issues</span></span>

<span data-ttu-id="de644-118">Если страница содержит изображения с размером более 300 КБ, щелкните результат **Обнаружены большие изображения**, чтобы увидеть, какие изображения являются слишком большими.</span><span class="sxs-lookup"><span data-stu-id="de644-118">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="de644-119">На современных страницах SharePoint Online представления изображений создаются автоматически с подбором размеров с учетом окна браузера и разрешения монитора клиента.</span><span class="sxs-lookup"><span data-stu-id="de644-119">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="de644-120">Перед отправкой в SharePoint Online всегда следует оптимизировать изображения для использования в Интернете.</span><span class="sxs-lookup"><span data-stu-id="de644-120">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="de644-121">Размеры и разрешение очень больших изображений автоматически уменьшаются, что может привести к непредвиденным параметрам представления.</span><span class="sxs-lookup"><span data-stu-id="de644-121">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="de644-122">Перед внесением изменений в страницы для исправления проблем с производительностью запомните время загрузки страницы в результатах анализа.</span><span class="sxs-lookup"><span data-stu-id="de644-122">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="de644-123">Снова запустите средство после изменения, чтобы увидеть, соответствует ли новый результат базовому стандарту, и проверить новое время загрузки на наличие улучшений.</span><span class="sxs-lookup"><span data-stu-id="de644-123">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Результаты времени загрузки страницы](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="de644-125">Время загрузки страницы зависит от множества факторов, например загрузки сети, времени суток и других переменных условий.</span><span class="sxs-lookup"><span data-stu-id="de644-125">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="de644-126">Следует несколько раз проверить время загрузки страницы до и после внесения изменений, чтобы получить средние результаты.</span><span class="sxs-lookup"><span data-stu-id="de644-126">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="de644-127">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="de644-127">Related topics</span></span>

[<span data-ttu-id="de644-128">Настройка производительности SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="de644-128">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="de644-129">Настройка производительности Office 365</span><span class="sxs-lookup"><span data-stu-id="de644-129">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="de644-130">Производительность в современном интерфейсе SharePoint</span><span class="sxs-lookup"><span data-stu-id="de644-130">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/ru-RU/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="de644-131">Сети доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="de644-131">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="de644-132">Использование сети доставки содержимого Office 365 с SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="de644-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
