---
title: Оптимизация веса страниц современных сайтов SharePoint Online
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
description: Узнайте, как оптимизировать вес страниц современных сайтов SharePoint Online.
ms.openlocfilehash: 5e2231468363f58faeac1d7b21e06cd4fa790cf8
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028216"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="c81ba-103">Оптимизация веса страниц современных сайтов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c81ba-103">Optimize page weight in SharePoint Online modern site pages</span></span>

<span data-ttu-id="c81ba-104">Страницы современного сайта SharePoint Online содержат сериализованный код, необходимый для отображения содержимого страницы, включая изображения, текст, объекты в области содержимого под панелью навигации или панелью команд, а также HTML-код для формирования структуры страницы.</span><span class="sxs-lookup"><span data-stu-id="c81ba-104">SharePoint Online modern site pages contain serialized code that is required to render page content of the page, including images, text, objects in the content area underneath navigation/command bars and other HTML code that forms the framework of the page.</span></span> <span data-ttu-id="c81ba-105">Вес страницы определяется этим HTML-кодом и должен быть ограничен, чтобы обеспечить оптимальное время загрузки страницы.</span><span class="sxs-lookup"><span data-stu-id="c81ba-105">Page weight is a measurement of this HTML code, and should be limited to ensure optimal page load times.</span></span>

<span data-ttu-id="c81ba-106">Эта статья поможет вам понять, как уменьшить вес страниц современного сайта.</span><span class="sxs-lookup"><span data-stu-id="c81ba-106">This article will help you understand how to reduce page weight in your modern site pages.</span></span>

>[!NOTE]
><span data-ttu-id="c81ba-107">Дополнительные сведения о производительности на современных порталах SharePoint Online см. в статье [Производительность в современном интерфейсе SharePoint](https://docs.microsoft.com/ru-RU/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="c81ba-107">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/ru-RU/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a><span data-ttu-id="c81ba-108">Использование средства диагностики страниц SharePoint для анализа веса страниц</span><span class="sxs-lookup"><span data-stu-id="c81ba-108">Use the Page Diagnostics for SharePoint tool to analyze page weight</span></span>

<span data-ttu-id="c81ba-109">Средство **Диагностика страниц SharePoint** — это браузерное расширение для Chrome и [Microsoft Edge версии 77 или более поздней](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8), которое можно использовать для анализа страниц современных и классических сайтов публикации SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c81ba-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="c81ba-110">Это средство предоставляет отчет о каждой проанализированной странице, показывающий, как страница работает в определенном наборе условий.</span><span class="sxs-lookup"><span data-stu-id="c81ba-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="c81ba-111">Чтобы установить и изучить средство диагностики страниц SharePoint, ознакомьтесь со статьей [Использование средства диагностики страниц SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="c81ba-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="c81ba-112">При анализе страницы сайта SharePoint с помощью средства диагностики страниц SharePoint вы можете просматривать сведения о странице в результате **Вес страницы до 500 КБ** на панели _Диагностические тесты_.</span><span class="sxs-lookup"><span data-stu-id="c81ba-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about page in the **Page weight under 500KB** result of the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="c81ba-113">Результат появится в зеленом цвете, если вес страницы ниже базового значения, и в красном, если вес страницы превышает базовое значение.</span><span class="sxs-lookup"><span data-stu-id="c81ba-113">The result will appear in green if the page weight is under the baseline value, and red if the page weight exceeds the baseline value.</span></span>

<span data-ttu-id="c81ba-114">Возможные результаты:</span><span class="sxs-lookup"><span data-stu-id="c81ba-114">Possible results include:</span></span>

- <span data-ttu-id="c81ba-115">**Внимание** (красный): вес страницы превышает 500 КБ</span><span class="sxs-lookup"><span data-stu-id="c81ba-115">**Attention required** (red): Page weight exceeds 500KB</span></span>
- <span data-ttu-id="c81ba-116">**Действия не требуются** (зеленый): вес страницы не превышает 500 КБ</span><span class="sxs-lookup"><span data-stu-id="c81ba-116">**No action required** (green): Page weight is under 500KB</span></span>

<span data-ttu-id="c81ba-117">Если результат **Вес страницы до 500 КБ** появляется в разделе **Внимание**, щелкните результат, чтобы получить дополнительные сведения.  </span><span class="sxs-lookup"><span data-stu-id="c81ba-117">If the **Page weight under 500KB** result appears in the **Attention required** section, you can click the result for details.</span></span>

![Результаты "Запросы к SharePoint"](media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a><span data-ttu-id="c81ba-119">Исправление проблем с весом страниц</span><span class="sxs-lookup"><span data-stu-id="c81ba-119">Remediate page weight issues</span></span>

<span data-ttu-id="c81ba-120">Если вес страницы превышает 500 КБ, общее время загрузки можно улучшить, уменьшая количество веб-частей и ограничивая содержимое страницы до соответствующего уровня. </span><span class="sxs-lookup"><span data-stu-id="c81ba-120">If page weight exceeds 500KB, you can improve overall page load time by reducing the number of web parts and limiting page content to an appropriate degree.</span></span>

<span data-ttu-id="c81ba-121">Общие инструкции по уменьшению веса страницы</span><span class="sxs-lookup"><span data-stu-id="c81ba-121">General guidance for reducing page weight includes:</span></span>

- <span data-ttu-id="c81ba-122">Ограничьте содержимое страницы до приемлемого размера и используйте несколько страниц для связанного контента.</span><span class="sxs-lookup"><span data-stu-id="c81ba-122">Limit the page content to a reasonable amount and use multiple pages for related content.</span></span>
- <span data-ttu-id="c81ba-123">Минимизируйте использование веб-частей с крупными контейнерами свойств.</span><span class="sxs-lookup"><span data-stu-id="c81ba-123">Minimize the use of web parts that have large property bags.</span></span>
- <span data-ttu-id="c81ba-124">По возможности используйте неинтерактивные представления сведений.</span><span class="sxs-lookup"><span data-stu-id="c81ba-124">Use non-interactive rollup views when possible.</span></span>
- <span data-ttu-id="c81ba-125">Оптимизируйте размеры изображений, изменяя их с помощью форматов сжатия и загружая их из CDN.</span><span class="sxs-lookup"><span data-stu-id="c81ba-125">Optimize image sizes by sizing images appropriately, using compressed image formats and ensuring that they are downloaded from a CDN.</span></span>

<span data-ttu-id="c81ba-126">Дополнительные инструкции по ограничению веса страницы можно найти в следующей статье:</span><span class="sxs-lookup"><span data-stu-id="c81ba-126">You can find additional guidance for limiting page weight in the following article:</span></span>

- [<span data-ttu-id="c81ba-127">Оптимизация производительности страниц в SharePoint</span><span class="sxs-lookup"><span data-stu-id="c81ba-127">Optimize page performance in SharePoint</span></span>](https://docs.microsoft.com/ru-RU/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

<span data-ttu-id="c81ba-128">Перед внесением изменений в страницы для исправления проблем с производительностью запомните время загрузки страницы в результатах анализа.</span><span class="sxs-lookup"><span data-stu-id="c81ba-128">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="c81ba-129">Снова запустите средство после изменения, чтобы увидеть, соответствует ли новый результат базовому стандарту, и проверить новое время загрузки на наличие улучшений.</span><span class="sxs-lookup"><span data-stu-id="c81ba-129">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Результаты времени загрузки страницы](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="c81ba-131">Время загрузки страницы зависит от множества факторов, например загрузки сети, времени суток и других переменных условий.</span><span class="sxs-lookup"><span data-stu-id="c81ba-131">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="c81ba-132">Следует несколько раз проверить время загрузки страницы до и после внесения изменений, чтобы получить средние результаты.</span><span class="sxs-lookup"><span data-stu-id="c81ba-132">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c81ba-133">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="c81ba-133">Related topics</span></span>

[<span data-ttu-id="c81ba-134">Настройка производительности SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c81ba-134">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="c81ba-135">Настройка производительности Office 365</span><span class="sxs-lookup"><span data-stu-id="c81ba-135">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="c81ba-136">Производительность в современном интерфейсе SharePoint</span><span class="sxs-lookup"><span data-stu-id="c81ba-136">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/ru-RU/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="c81ba-137">Сети доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="c81ba-137">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="c81ba-138">Использование сети доставки содержимого Office 365 с SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c81ba-138">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
