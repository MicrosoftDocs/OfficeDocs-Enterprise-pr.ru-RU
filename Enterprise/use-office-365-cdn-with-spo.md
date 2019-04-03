---
title: Использование сети доставки содержимого Office 365 с SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: В этой статье описывается использование сети доставки содержимого (CDN) Office 365 для ускорения доставки ресурсов SharePoint Online всем пользователям независимо от того, где они размещены, или от того, как они обращаются к контенту.
ms.openlocfilehash: a718c30a40209a8ee0c8e78700ed3eae72c8347c
ms.sourcegitcommit: 43d2b7e1d9932182c6cca5164d4d9096dcf4ed36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "31039506"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="8a37e-103">Использование сети доставки содержимого Office 365 с SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="8a37e-104">Вы можете использовать встроенную сеть доставки содержимого (CDN) Office 365 для размещения статических ресурсов, чтобы повысить производительность страниц SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="8a37e-105">Сеть CDN Office 365 повышает производительность путем кэширования статических ресурсов ближе к браузерам, которые их запрашивают, что повышает скорость скачиваний и снижает задержку.</span><span class="sxs-lookup"><span data-stu-id="8a37e-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="8a37e-106">Кроме того, в сети CDN Office 365 используется [протокол HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) для улучшения сжатия и конвейерной передачи данных по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="8a37e-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="8a37e-107">Служба CDN Office 365 входит в состав подписки на SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="8a37e-108">Сети доставки содержимого Office 365 состоит из нескольких сетей CDN, позволяющих размещать статические ресурсы в нескольких расположениях или _источниках_ и использовать их из глобальных высокоскоростных сетей.</span><span class="sxs-lookup"><span data-stu-id="8a37e-108">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="8a37e-109">В зависимости от типа содержимого, которое необходимо разместить в сети CDN Office 365, можно добавить **общедоступные** источники, **закрытые** источники или оба варианта.</span><span class="sxs-lookup"><span data-stu-id="8a37e-109">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="8a37e-110">В этой статье описывается [способ определения того, является ли источник общедоступным или частным](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) для дополнительной информации о различиях между общедоступными и частными происхождениями.</span><span class="sxs-lookup"><span data-stu-id="8a37e-110">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="8a37e-111">![Концептуальная схема CDN для Office 365] (media/O365-CDN/o365-cdn-flow-transparent.svg "Концептуальная схема CDN для Office 365")</span><span class="sxs-lookup"><span data-stu-id="8a37e-111">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="8a37e-112">Если вы уже знакомы с тем, как работает сети CDN, вам нужно выполнить лишь несколько действий, чтобы включить CDN Office 365 для клиента.</span><span class="sxs-lookup"><span data-stu-id="8a37e-112">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="8a37e-113">В этом разделе описывается, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="8a37e-113">This topic describes how.</span></span> <span data-ttu-id="8a37e-114">Сведения о том, как приступить к размещению статических ресурсов, можно узнать в статье.</span><span class="sxs-lookup"><span data-stu-id="8a37e-114">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="8a37e-115">Существуют другие размещенные в Майкрософт сети CDN, которые можно использовать с Office 365 для специализированных сценариев использования, но не рассматриваются в этом разделе, так как они выходят за границы области CDN Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a37e-115">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="8a37e-116">Для получения дополнительных сведений обратитесь к разделу [Microsoft сети CDN](content-delivery-networks.md#other-microsoft-cdns).</span><span class="sxs-lookup"><span data-stu-id="8a37e-116">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 **<span data-ttu-id="8a37e-117">Перейдите обратно к [планированИю сети и настройке производительности для Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="8a37e-117">Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="8a37e-118">Общие сведения о работе с CDN Office 365 в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-118">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="8a37e-119">Чтобы настроить CDN Office 365 для Организации, выполните следующие основные действия.</span><span class="sxs-lookup"><span data-stu-id="8a37e-119">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

- [<span data-ttu-id="8a37e-120">Планирование развертывания сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-120">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - <span data-ttu-id="8a37e-121">[Определите, какие статические ресурсы необходимо разместить в сети CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span><span class="sxs-lookup"><span data-stu-id="8a37e-121">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  - <span data-ttu-id="8a37e-122">[Определите, где вы хотите хранить ресурсы](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span><span class="sxs-lookup"><span data-stu-id="8a37e-122">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="8a37e-123">Это расположение может быть сайтом, библиотекой или папкой SharePoint и называется _источником_.</span><span class="sxs-lookup"><span data-stu-id="8a37e-123">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  - <span data-ttu-id="8a37e-124">[Выберите, должен ли каждый источник быть общедоступным или частным](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span><span class="sxs-lookup"><span data-stu-id="8a37e-124">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="8a37e-125">Вы можете добавить несколько начальных версий для общедоступных и частных типов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-125">You can add multiple origins of both public and private types.</span></span>

- <span data-ttu-id="8a37e-126">Установка и настройка сети CDN с помощью PowerShell или CLI в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-126">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  - [<span data-ttu-id="8a37e-127">Установка и настройка сети CDN с помощью командной консоли SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-127">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [<span data-ttu-id="8a37e-128">Установка и настройка сети CDN с помощью интерфейса командной строки Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-128">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="8a37e-129">После выполнения этого действия будут выполнены следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8a37e-129">When you complete this step, you will have:</span></span>

  - <span data-ttu-id="8a37e-130">Включена сеть CDN для Организации.</span><span class="sxs-lookup"><span data-stu-id="8a37e-130">Enabled the CDN for your organization.</span></span>
  - <span data-ttu-id="8a37e-131">Добавлены источники, идентифицирующие каждый источник как общедоступный или частный.</span><span class="sxs-lookup"><span data-stu-id="8a37e-131">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="8a37e-132">После завершения установки вы сможете [управлять CDN Office 365](use-office-365-cdn-with-spo.md#CDNManage) по времени, выполнив следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8a37e-132">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
- <span data-ttu-id="8a37e-133">Добавление, обновление и удаление активов</span><span class="sxs-lookup"><span data-stu-id="8a37e-133">Adding, updating, and removing assets</span></span>
- <span data-ttu-id="8a37e-134">Добавление и удаление источников</span><span class="sxs-lookup"><span data-stu-id="8a37e-134">Adding and removing origins</span></span>
- <span data-ttu-id="8a37e-135">Настройка политик CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-135">Configuring CDN policies</span></span>
- <span data-ttu-id="8a37e-136">При необходимости отключение сети CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-136">If necessary, disabling the CDN</span></span>

<span data-ttu-id="8a37e-137">Наконец, ознакомьтесь с разделом [использование ресурсов CDN](use-office-365-cdn-with-spo.md#using-your-cdn-assets) для получения сведений о доступе к ресурсам CDN как из общедоступных, так и из частных источников.</span><span class="sxs-lookup"><span data-stu-id="8a37e-137">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="8a37e-138">Рекомендации по устранению распространенных проблем приведены [в разделе устраненИе неполадок в сети CDN Office 365](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="8a37e-138">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="8a37e-139">Планирование развертывания сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-139">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="8a37e-140">Перед развертыванием сети CDN Office 365 для клиента Office 365 необходимо учесть следующие факторы в процессе планирования.</span><span class="sxs-lookup"><span data-stu-id="8a37e-140">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  - [<span data-ttu-id="8a37e-141">Определение статических ресурсов, которые необходимо разместить в сети CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-141">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  - [<span data-ttu-id="8a37e-142">Определение места хранения активов</span><span class="sxs-lookup"><span data-stu-id="8a37e-142">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [<span data-ttu-id="8a37e-143">Выберите, должен ли каждый источник быть общедоступным или частным</span><span class="sxs-lookup"><span data-stu-id="8a37e-143">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="8a37e-144">Определение статических ресурсов, которые необходимо разместить в сети CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-144">Determine which static assets you want to host on the CDN</span></span>
<a name="CDNAssets"> </a>

<span data-ttu-id="8a37e-145">Как правило, сети CDN наиболее эффективны для хостинга _статических ресурсов_или ресурсов, которые не меняются очень часто.</span><span class="sxs-lookup"><span data-stu-id="8a37e-145">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="8a37e-146">Хорошее правило для параметра Thumb — определить файлы, которые удовлетворяют некоторым или всем указанным ниже условиям.</span><span class="sxs-lookup"><span data-stu-id="8a37e-146">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

- <span data-ttu-id="8a37e-147">Статические файлы, встроенные в страницу (например, сценарии и изображения), которые могут значительно повлиять на время загрузки страницы.</span><span class="sxs-lookup"><span data-stu-id="8a37e-147">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
- <span data-ttu-id="8a37e-148">Большие файлы, такие как исполняемые файлы и файлы установки</span><span class="sxs-lookup"><span data-stu-id="8a37e-148">Large files like executables and installation files</span></span>
- <span data-ttu-id="8a37e-149">Потоковые файлы мультимедиа</span><span class="sxs-lookup"><span data-stu-id="8a37e-149">Streaming media files</span></span>
- <span data-ttu-id="8a37e-150">Библиотеки ресурсов, поддерживающие код на стороне клиента</span><span class="sxs-lookup"><span data-stu-id="8a37e-150">Resource libraries that support client-side code</span></span>

<span data-ttu-id="8a37e-151">Например, небольшие файлы, которые часто запрашиваются как изображения и сценарии, могут значительно повысить производительность визуализации сайта и постепенно уменьшить нагрузку на сайты SharePoint Online при добавлении их в источник CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-151">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="8a37e-152">Большие файлы, такие как исполняемые файлы установки или видеофайлы, можно загружать или переносить из сети CDN, обеспечивая положительное воздействие на производительность и последующее сокращение нагрузки на сайт SharePoint Online, даже если они не обращаются к ним часто.</span><span class="sxs-lookup"><span data-stu-id="8a37e-152">Larger files such as installation executables or video files can be downloaded or streamed from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="8a37e-153">Повышение производительности для отдельных файлов зависит от многих факторов, включая расстояние от клиента до ближайшей конечной точки CDN, временные условия локальной сети и т. д.</span><span class="sxs-lookup"><span data-stu-id="8a37e-153">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="8a37e-154">Многие статические файлы довольно малы, и их можно скачать из Office 365 менее чем через секунду.</span><span class="sxs-lookup"><span data-stu-id="8a37e-154">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="8a37e-155">Однако веб-страница может содержать множество внедренных файлов с накопительным временем загрузки в несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="8a37e-155">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="8a37e-156">Обслуживание этих файлов из сети CDN может значительно снизить общее время загрузки страницы.</span><span class="sxs-lookup"><span data-stu-id="8a37e-156">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="8a37e-157">Узнайте, [какой выигрыш в производительности обеспечивает сеть CDN?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) в качестве примера.</span><span class="sxs-lookup"><span data-stu-id="8a37e-157">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="8a37e-158">Определение места хранения активов</span><span class="sxs-lookup"><span data-stu-id="8a37e-158">Determine where you want to store your assets</span></span>
<a name="CDNStoreAssets"> </a>

<span data-ttu-id="8a37e-159">CDN извлекает ресурсы из расположения, называемого _источником_.</span><span class="sxs-lookup"><span data-stu-id="8a37e-159">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="8a37e-160">Источником может быть сайт SharePoint, Библиотека документов или папка, доступ к которым можно получить по URL-АДРЕСу.</span><span class="sxs-lookup"><span data-stu-id="8a37e-160">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="8a37e-161">При указании источников для организации вы можете обеспечить высокую гибкость.</span><span class="sxs-lookup"><span data-stu-id="8a37e-161">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="8a37e-162">Например, вы можете указать несколько источников или один источник, где будут размещаться все ресурсы CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-162">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="8a37e-163">Вы можете использовать как общедоступные, так и частные источники для Организации.</span><span class="sxs-lookup"><span data-stu-id="8a37e-163">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="8a37e-164">В большинстве организаций будет выбрана комбинация этих двух интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-164">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="8a37e-165">Вы можете создать новый контейнер для таких источников, как папки или библиотеки документов, а также добавить файлы, которые необходимо сделать доступными из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-165">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="8a37e-166">Это хороший подход, если у вас есть определенный набор ресурсов, который должен быть доступен из сети CDN, и необходимо ограничить набор ресурсов CDN только теми файлами, которые находятся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="8a37e-166">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="8a37e-167">Вы также можете настроить существующее семейство веб-сайтов, сайт, библиотеку или папку в качестве источника, что сделает все подходящие ресурсы в контейнере доступными из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-167">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="8a37e-168">Перед добавлением существующего контейнера в качестве источника необходимо убедиться, что вы осведомлены о его содержимом и разрешениях, чтобы случайно не предоставить ресурсы для анонимного доступа или неавторизованных пользователей.</span><span class="sxs-lookup"><span data-stu-id="8a37e-168">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="8a37e-169">Вы можете определить _политики CDN_ , чтобы исключить контент из источников CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-169">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="8a37e-170">Политики CDN исключают ресурсы в общедоступных или закрытых источниках с помощью таких атрибутов, как _Тип файла_ и _классификация сайтов_, и применяются ко всем источникам кднтипе (частных или общедоступных), заданным в политике.</span><span class="sxs-lookup"><span data-stu-id="8a37e-170">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="8a37e-171">Например, если вы добавляете частный источник, состоящий из сайта, который содержит несколько дочерних сайтов, можно определить политику, чтобы исключить сайты, помеченные как **конфиденциальные** , чтобы содержимое с сайтов с такой классификацией не было доставлено из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-171">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="8a37e-172">Политика будет применяться к содержимому _всех_ частных источников, добавленных в CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-172">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="8a37e-173">Имейте в виду, что чем больше происхождений, тем выше влияние на время, которое использует служба CDN для обработки запросов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-173">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="8a37e-174">Мы рекомендуем ограничить количество происхождений максимально возможной.</span><span class="sxs-lookup"><span data-stu-id="8a37e-174">We recommend that you limit the number of origins as much as possible.</span></span>
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="8a37e-175">Выберите, должен ли каждый источник быть общедоступным или частным</span><span class="sxs-lookup"><span data-stu-id="8a37e-175">Choose whether each origin should be public or private</span></span>
<a name="CDNOriginChoosePublicPrivate"> </a>

<span data-ttu-id="8a37e-176">При определении источника необходимо указать, следует ли сделать его общедоступным __ или _частным_.</span><span class="sxs-lookup"><span data-stu-id="8a37e-176">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="8a37e-177">Доступ к ресурсам CDN в общедоступных источниках анонимен, а содержимое CDN в частных источниках защищено динамически создаваемыми маркерами для повышения безопасности.</span><span class="sxs-lookup"><span data-stu-id="8a37e-177">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="8a37e-178">Независимо от того, какой вариант выбран, корпорация Майкрософт выполняет всю тяжелую тяжелую работы, когда речь идет об администрировании самой сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-178">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="8a37e-179">Вы также можете изменить свое предположение позже, после того как вы настроили сеть CDN и определили происхождение.</span><span class="sxs-lookup"><span data-stu-id="8a37e-179">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="8a37e-180">Общедоступные и частные параметры обеспечивают одинаковый выигрыш в производительности, но каждый из них имеет уникальные атрибуты и преимущества.</span><span class="sxs-lookup"><span data-stu-id="8a37e-180">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="8a37e-181">\*\*\*\* Общедоступные источники в сети CDN Office 365 доступны анонимно, а размещенные ресурсы доступны всем пользователям, у которых есть URL-адрес актива.</span><span class="sxs-lookup"><span data-stu-id="8a37e-181">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="8a37e-182">Так как доступ к содержимому в общедоступных источниках является анонимным, следует использовать их только для кэширования неконфиденциального общего содержимого, например файлов JavaScript, скриптов, значков и изображений.</span><span class="sxs-lookup"><span data-stu-id="8a37e-182">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="8a37e-183">**Закрытые** источники в сети CDN Office 365 обеспечивают закрытый доступ к пользовательскому содержимому, такому как библиотеки документов SharePoint Online, сайты и мультимедиа, например видео.</span><span class="sxs-lookup"><span data-stu-id="8a37e-183">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and media such as videos.</span></span> <span data-ttu-id="8a37e-184">Доступ к содержимому в частных источниках обеспечивается динамически созданными маркерами, поэтому доступ к ним могут получать только пользователи с разрешениями на исходную библиотеку документов или место хранения.</span><span class="sxs-lookup"><span data-stu-id="8a37e-184">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="8a37e-185">Частные источники в сети CDN Office 365 можно использовать только для контента SharePoint Online, и доступ к ресурсам в частных источниках можно получить через перенаправление из клиента SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-185">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="8a37e-186">Дополнительные сведения о доступе CDN к активам в частном источнике работают при [использовании ресурсов в частных источниках](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span><span class="sxs-lookup"><span data-stu-id="8a37e-186">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="8a37e-187">Атрибуты и преимущества хостинга активов в общедоступных источниках</span><span class="sxs-lookup"><span data-stu-id="8a37e-187">Attributes and advantages of hosting assets in public origins</span></span>
  
- <span data-ttu-id="8a37e-188">Ресурсы, предоставляемые из общедоступного источника, доступны всем анонимно.</span><span class="sxs-lookup"><span data-stu-id="8a37e-188">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="8a37e-189">Никогда не следует размещать ресурсы, содержащие сведения о пользователях, или которые считаются конфиденциальными в Организации в общедоступном источнике.</span><span class="sxs-lookup"><span data-stu-id="8a37e-189">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
- <span data-ttu-id="8a37e-190">Если удалить ресурс из общедоступного источника, он может оставаться доступным в кэше до 30 дней. Однако ссылки на ресурс в сети CDN станут недействительными в течение 15 минут.</span><span class="sxs-lookup"><span data-stu-id="8a37e-190">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
- <span data-ttu-id="8a37e-191">При размещении таблиц стилей (CSS-файлов) в общедоступном источнике можно использовать в коде относительные пути и URI.</span><span class="sxs-lookup"><span data-stu-id="8a37e-191">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="8a37e-192">Это означает, что вы можете ссылаться на расположение фоновых изображений и других объектов относительно расположения ресурса, который вызывает его.</span><span class="sxs-lookup"><span data-stu-id="8a37e-192">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
- <span data-ttu-id="8a37e-193">Вы можете жестко задать URL-адрес общедоступного источника, но это не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="8a37e-193">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="8a37e-194">Это связано с тем, что если сеть CDN станет недоступна, то URL-адрес не будет автоматически указывать на вашу организацию в SharePoint Online, что может привести к неработоспособности ссылок и другим ошибкам.</span><span class="sxs-lookup"><span data-stu-id="8a37e-194">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
- <span data-ttu-id="8a37e-195">По умолчанию для общедоступных источников включены типы файлов CSS, EOT, GIF, ICO, JPEG, JPG, JS, MAP, PNG, SVG, TTF и WOFF.</span><span class="sxs-lookup"><span data-stu-id="8a37e-195">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="8a37e-196">Вы можете указать дополнительные типы файлов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-196">You can specify additional file types.</span></span>
- <span data-ttu-id="8a37e-197">Вы можете настроить политику, чтобы исключить ресурсы, которые были определены классификациями сайтов, которые вы указали.</span><span class="sxs-lookup"><span data-stu-id="8a37e-197">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="8a37e-198">Например, вы можете исключать все ресурсы, отмеченные как "конфиденциальные" или "с ограниченным доступом", даже если они относятся к разрешенным типам файлов и находятся в общедоступном источнике.</span><span class="sxs-lookup"><span data-stu-id="8a37e-198">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="8a37e-199">Атрибуты и преимущества хостинга активов в частных источниках</span><span class="sxs-lookup"><span data-stu-id="8a37e-199">Attributes and advantages of hosting assets in private origins</span></span>

- <span data-ttu-id="8a37e-200">Частные источники можно использовать только для ресурсов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-200">Private origins can only be used for SharePoint Online assets.</span></span>
- <span data-ttu-id="8a37e-201">Пользователи могут получать доступ к ресурсам из частного источника, только если у них есть разрешения на доступ к контейнеру.</span><span class="sxs-lookup"><span data-stu-id="8a37e-201">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="8a37e-202">Анонимный доступ к таким ресурсам запрещен.</span><span class="sxs-lookup"><span data-stu-id="8a37e-202">Anonymous access to these assets is prevented.</span></span>
- <span data-ttu-id="8a37e-203">Ресурсы в частных источниках должны ссылаться на клиента SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-203">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="8a37e-204">Прямой доступ к ресурсам частной сети CDN не работает.</span><span class="sxs-lookup"><span data-stu-id="8a37e-204">Direct access to private CDN assets does not work.</span></span>
- <span data-ttu-id="8a37e-205">При удалении актива из частного источника ресурс может продолжать быть доступен в течение часа из кэша; Однако мы сделаете ссылки на ресурс в сети CDN недействительными в течение 15 минут после удаления актива.</span><span class="sxs-lookup"><span data-stu-id="8a37e-205">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
- <span data-ttu-id="8a37e-206">По умолчанию для частных источников включены типы файлов GIF, ICO, JPEG, JPG, JS и PNG.</span><span class="sxs-lookup"><span data-stu-id="8a37e-206">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="8a37e-207">Вы можете указать дополнительные типы файлов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-207">You can specify additional file types.</span></span>
- <span data-ttu-id="8a37e-208">Как и в случае с общедоступными источниками, вы можете настроить политику, чтобы исключить ресурсы, идентифицированные с помощью классификаций сайтов, которые вы указали, даже если вы используете подстановочные знаки, чтобы включить все ресурсы в папке или библиотеке документов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-208">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="8a37e-209">Дополнительные сведения об использовании сети CDN Office 365, основных концепций CDN и других сети CDN, которые можно использовать в клиенте Office 365, можно найти в статье [Доставка содержимого](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="8a37e-209">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="8a37e-210">Источники CDN по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8a37e-210">Default CDN origins</span></span>

<span data-ttu-id="8a37e-211">Если вы не укажете иное, Office 365 настроит некоторые источники по умолчанию при включении сети CDN Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a37e-211">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="8a37e-212">Если вы изначально не хотите предоставлять их, вы можете добавить эти источники после завершения установки.</span><span class="sxs-lookup"><span data-stu-id="8a37e-212">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="8a37e-213">Если вы не знакомы с последствиями для пропуска настройки источников по умолчанию и по этой причине, необходимо разрешить их создание при включении сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-213">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="8a37e-214">Источники частной сети CDN по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="8a37e-214">Default private CDN origins:</span></span>
  
- <span data-ttu-id="8a37e-215">\*/усерфото.аспкс</span><span class="sxs-lookup"><span data-stu-id="8a37e-215">\*/userphoto.aspx</span></span>
- <span data-ttu-id="8a37e-216">\*/ситеассетс</span><span class="sxs-lookup"><span data-stu-id="8a37e-216">\*/siteassets</span></span>

<span data-ttu-id="8a37e-217">Источники общедоступной сети CDN по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="8a37e-217">Default public CDN origins:</span></span>
  
- <span data-ttu-id="8a37e-218">\*/мастерпаже</span><span class="sxs-lookup"><span data-stu-id="8a37e-218">\*/masterpage</span></span>
- <span data-ttu-id="8a37e-219">\*Библиотека/Style Library</span><span class="sxs-lookup"><span data-stu-id="8a37e-219">\*/style library</span></span>
- <span data-ttu-id="8a37e-220">\*/клиентсидеассетс</span><span class="sxs-lookup"><span data-stu-id="8a37e-220">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="8a37e-221">_клиентсидеассетс_ — это общедоступный источник, добавленный в службу CDN Office 365 за декабрь 2017.</span><span class="sxs-lookup"><span data-stu-id="8a37e-221">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="8a37e-222">Этот источник должен присутствовать, чтобы решения SharePoint Framework в сети CDN работали.</span><span class="sxs-lookup"><span data-stu-id="8a37e-222">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="8a37e-223">Если вы включили CDN Office 365 до 2017 декабря, или если вы пропустили настройку источников по умолчанию при включении сети CDN, вы можете добавить этот источник вручную.</span><span class="sxs-lookup"><span data-stu-id="8a37e-223">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="8a37e-224">Дополнительные сведения см. в статье [Моя клиентская веб-часть или решение SharePoint Framework не работает](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span><span class="sxs-lookup"><span data-stu-id="8a37e-224">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="8a37e-225">Установка и настройка сети CDN Office 365 с помощью командной консоли SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-225">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>
<a name="CDNSetupinPShell"> </a>

<span data-ttu-id="8a37e-226">Процедуры, описанные в этом разделе, требуют использования командной консоли SharePoint Online для подключения к SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-226">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="8a37e-227">Инструкции см. в статье [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="8a37e-227">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="8a37e-228">Выполните указанные ниже действия, чтобы настроить и настроить сеть CDN для размещения ресурсов в SharePoint Online с помощью командной консоли SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-228">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="8a37e-229">Предоставление Организации разрешения на использование сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-229">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="8a37e-230">Перед внесением изменений в параметры CDN клиента необходимо получить текущее состояние конфигурации частной сети CDN в клиенте Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a37e-230">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="8a37e-231">Подключитесь к клиенту с помощью командной консоли SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="8a37e-231">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="8a37e-232">Теперь используйте командлет **Get – SPOTenantCdnEnabled** для получения параметров состояния CDN из клиента:</span><span class="sxs-lookup"><span data-stu-id="8a37e-232">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="8a37e-233">Состояние сети CDN для указанного Кднтипе будет выведено на экран.</span><span class="sxs-lookup"><span data-stu-id="8a37e-233">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="8a37e-234">Используйте командлет **Set – SPOTenantCdnEnabled** , чтобы разрешить Организации использовать CDN Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a37e-234">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="8a37e-235">Вы можете разрешить Организации использовать общедоступные источники, частные источники или и то, и другое одновременно.</span><span class="sxs-lookup"><span data-stu-id="8a37e-235">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="8a37e-236">Кроме того, можно настроить CDN для пропуска настройки источников по умолчанию при включении.</span><span class="sxs-lookup"><span data-stu-id="8a37e-236">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="8a37e-237">Вы всегда можете добавить эти источники позже, как описано в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="8a37e-237">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="8a37e-238">В Windows PowerShell для SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="8a37e-238">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="8a37e-239">Например, чтобы разрешить в Организации использование общедоступных и частных источников, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-239">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="8a37e-240">Чтобы разрешить в Организации использование общедоступных и частных источников, но пропустить настройку по умолчанию, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-240">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="8a37e-241">Сведения [](use-office-365-cdn-with-spo.md#default-cdn-origins) об источниках, подготовленных по умолчанию при включенИИ сети cdn Office 365, и потенциальном влиянии на пропуск настройки источников по умолчанию см.</span><span class="sxs-lookup"><span data-stu-id="8a37e-241">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="8a37e-242">Чтобы разрешить в Организации использование общедоступных источников, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-242">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="8a37e-243">Чтобы разрешить Организации использовать частные источники, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-243">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="8a37e-244">Дополнительные сведения об этом командлете приведены в разделе [Set – SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-244">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="8a37e-245">Изменение списка типов файлов, включаемых в CDN Office 365 (неОбязательно)</span><span class="sxs-lookup"><span data-stu-id="8a37e-245">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> <span data-ttu-id="8a37e-246">При определении типов файлов с помощью командлета **Set – SPOTenantCdnPolicy** , заданный в текущий момент список перезаписывается.</span><span class="sxs-lookup"><span data-stu-id="8a37e-246">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="8a37e-247">Если вы хотите добавить в список дополнительные типы файлов, сначала воспользуйтесь командлетом, чтобы узнать, какие типы файлов уже разрешены и включить их в список вместе с новыми.</span><span class="sxs-lookup"><span data-stu-id="8a37e-247">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="8a37e-248">Используйте командлет **Set – SPOTenantCdnPolicy** , чтобы определить статические типы файлов, которые могут размещаться в сети CDN, а также в общедоступных и частных источниках.</span><span class="sxs-lookup"><span data-stu-id="8a37e-248">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="8a37e-249">По умолчанию разрешены типы стандартных активов, например CSS, GIF, JPG и JS.</span><span class="sxs-lookup"><span data-stu-id="8a37e-249">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="8a37e-250">В Windows PowerShell для SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="8a37e-250">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="8a37e-251">Например, чтобы разрешить сети CDN размещать файлы CSS и PNG, необходимо ввести следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-251">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="8a37e-252">Чтобы узнать, какие типы файлов в данный момент разрешены в сети CDN, используйте командлет **Get – SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="8a37e-252">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="8a37e-253">Дополнительные сведения об этих командлетах приведены в статье [Set/SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) и [Get – SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-253">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="8a37e-254">Изменение списка классификаций сайтов, которые требуется исключить из сети CDN Office 365 (неОбязательно)</span><span class="sxs-lookup"><span data-stu-id="8a37e-254">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> <span data-ttu-id="8a37e-255">При исключении классификаций сайтов с помощью командлета **Set-SPOTenantCdnPolicy** заданный в текущий момент список перезаписывается.</span><span class="sxs-lookup"><span data-stu-id="8a37e-255">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="8a37e-256">Если требуется исключить дополнительные классификации сайтов, используйте командлет сначала, чтобы узнать, какие классификации уже исключены, а затем добавить их вместе с новыми.</span><span class="sxs-lookup"><span data-stu-id="8a37e-256">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="8a37e-257">Чтобы исключить классификации сайтов, которые не должны быть доступны в сети CDN, используйте командлет **Set-SPOTenantCdnPolicy**.</span><span class="sxs-lookup"><span data-stu-id="8a37e-257">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="8a37e-258">По умолчанию не исключаются никакие классификации сайтов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-258">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="8a37e-259">В Windows PowerShell для SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="8a37e-259">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="8a37e-260">Чтобы узнать, какие классификации сайтов в настоящее время ограничены, используйте командлет **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="8a37e-260">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="8a37e-261">Возвращаемые свойства: _инклудефиликстенсионс_, _ексклудерестриктедситеклассификатионс_ и _ексклудеифноскриптдисаблед_.</span><span class="sxs-lookup"><span data-stu-id="8a37e-261">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="8a37e-262">Свойство _инклудефиликстенсионс_ содержит список расширений файлов, которые будут обслуживаться из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-262">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="8a37e-263">Расширения файлов по умолчанию отличаются от общедоступных и закрытых.</span><span class="sxs-lookup"><span data-stu-id="8a37e-263">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="8a37e-264">Свойство _ексклудерестриктедситеклассификатионс_ содержит классификации сайтов, которые необходимо исключить из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-264">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="8a37e-265">Например, вы можете исключить сайты, помеченные \*\*\*\* как конфиденциальные, чтобы контент с сайтов, к которым применяется эта классификация, не был обслужен из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-265">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="8a37e-266">Свойство _ексклудеифноскриптдисаблед_ исключает содержимое из сети CDN на основе параметров атрибута _PostScript_ уровня сайта.</span><span class="sxs-lookup"><span data-stu-id="8a37e-266">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="8a37e-267">По умолчанию атрибуту InAttribute присвоено значение **Enabled** для _современных_ сайтов и **отключено** для __ _классических_ сайтов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-267">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="8a37e-268">Это зависит от параметров клиента.</span><span class="sxs-lookup"><span data-stu-id="8a37e-268">This depends on your tenant settings.</span></span>

<span data-ttu-id="8a37e-269">Дополнительные сведения об этих командлетах приведены в статье [Set/SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) и [Get – SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-269">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="8a37e-270">Добавление источника для ресурсов</span><span class="sxs-lookup"><span data-stu-id="8a37e-270">Add an origin for your assets</span></span>
<a name="Office365CDNforSPOOrigin"> </a>

<span data-ttu-id="8a37e-271">Используйте командлет **Add – SPOTenantCdnOrigin** , чтобы определить источник.</span><span class="sxs-lookup"><span data-stu-id="8a37e-271">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="8a37e-272">Вы можете определить несколько источников.</span><span class="sxs-lookup"><span data-stu-id="8a37e-272">You can define multiple origins.</span></span> <span data-ttu-id="8a37e-273">Источник — это URL-адрес, указывающий на библиотеку или папку в SharePoint, содержащую ресурсы, которые требуется размещать в сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-273">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="8a37e-274">Никогда не следует размещать ресурсы, содержащие сведения о пользователях, или которые считаются конфиденциальными в Организации в общедоступном источнике.</span><span class="sxs-lookup"><span data-stu-id="8a37e-274">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="8a37e-275">Значение _path_ — это путь к библиотеке или папке, в которой содержатся ресурсы.</span><span class="sxs-lookup"><span data-stu-id="8a37e-275">The value of _path_ is the path to the library or folder that contains the assets.</span></span> <span data-ttu-id="8a37e-276">Помимо относительных путей, можно использовать подстановочные знаки.</span><span class="sxs-lookup"><span data-stu-id="8a37e-276">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="8a37e-277">Источники поддерживают подстановочные знаки, добавленные к URL-АДРЕСу.</span><span class="sxs-lookup"><span data-stu-id="8a37e-277">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="8a37e-278">Это позволяет создавать источники, охватывающие несколько сайтов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-278">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="8a37e-279">Например, чтобы включить все ресурсы в папку masterpages для всех сайтов в качестве общедоступного источника в сети CDN, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-279">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- <span data-ttu-id="8a37e-280">Модификатор подстановочного знака \***/** можно использовать только в начале пути и будет соответствовать всем СЕГМЕНТАМ URL-адресов по УКАЗАНному URL-адресу.</span><span class="sxs-lookup"><span data-stu-id="8a37e-280">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
- <span data-ttu-id="8a37e-281">Путь может указывает на библиотеку документов, папку или сайт.</span><span class="sxs-lookup"><span data-stu-id="8a37e-281">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="8a37e-282">Например, путь _\*/site1_ будет сопоставлен всем библиотекам документов на сайте.</span><span class="sxs-lookup"><span data-stu-id="8a37e-282">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="8a37e-283">Вы можете добавить источник с определенным путем, используя относительный или полный путь.</span><span class="sxs-lookup"><span data-stu-id="8a37e-283">You can add an origin with a specific path using either a relative path or a full path.</span></span>

<span data-ttu-id="8a37e-284">В этом примере показано, как добавить закрытый источник библиотеки ситеассетс на определенном сайте, используя относительный путь:</span><span class="sxs-lookup"><span data-stu-id="8a37e-284">This example adds a private origin of the siteassets library on a specific site using a relative path:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="8a37e-285">В этом примере показано, как добавить частный источник папки _folder1_ в библиотеку активов семейства веб-сайтов с использованием полного пути:</span><span class="sxs-lookup"><span data-stu-id="8a37e-285">This example adds a private origin of the _folder1_ folder in the site collection's site assets library using the full path:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “https://contoso.sharepoint.com/sites/test/siteassets/folder1”
```

<span data-ttu-id="8a37e-286">Дополнительные сведения об этой команде и ее синтаксисе можно найти в статье [Add/SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-286">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="8a37e-287">В закрытых источниках ресурсы, к которым предоставлен общий доступ из источника, должны иметь основную версию, которая будет опубликована, прежде чем к ним можно будет получить доступ из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-287">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="8a37e-288">После выполнения команды система синхронизирует конфигурацию в центре обработки данных.</span><span class="sxs-lookup"><span data-stu-id="8a37e-288">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="8a37e-289">Это может занять до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="8a37e-289">This can take up to 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="8a37e-290">Пример: настройка общедоступного источника для главных страниц и библиотеки стилей для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-290">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<a name="ExamplePublicOrigin"> </a>

<span data-ttu-id="8a37e-291">Обычно эти источники настраиваются по умолчанию при включении сети CDN Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a37e-291">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="8a37e-292">Тем не менее, если вы хотите включить их вручную, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="8a37e-292">However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="8a37e-293">Используйте командлет **Add – SPOTenantCdnOrigin** , чтобы определить библиотеку стилей в качестве общедоступного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-293">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="8a37e-294">Используйте командлет **Add – SPOTenantCdnOrigin** , чтобы определить главные страницы в качестве общедоступного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-294">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="8a37e-295">Дополнительные сведения об этой команде и ее синтаксисе можно найти в статье [Add/SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-295">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="8a37e-296">После выполнения команды система синхронизирует конфигурацию в центре обработки данных.</span><span class="sxs-lookup"><span data-stu-id="8a37e-296">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="8a37e-297">Это может занять до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="8a37e-297">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="8a37e-298">Пример: Настройка частного источника для ресурсов сайта, страниц сайта и образов публикации для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-298">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<a name="ExamplePrivateOrigin"> </a>

- <span data-ttu-id="8a37e-299">Используйте командлет **Add-SPOTenantCdnOrigin** , чтобы определить папку ресурсов сайта в качестве частного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-299">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="8a37e-300">Используйте командлет **Add-SPOTenantCdnOrigin** , чтобы определить папку страниц сайта в качестве частного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-300">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="8a37e-301">Используйте командлет **Add – SPOTenantCdnOrigin** , чтобы определить папку "изображения публикации" в качестве частного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-301">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="8a37e-302">Дополнительные сведения об этой команде и ее синтаксисе можно найти в статье [Add/SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-302">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="8a37e-303">После выполнения команды система синхронизирует конфигурацию в центре обработки данных.</span><span class="sxs-lookup"><span data-stu-id="8a37e-303">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="8a37e-304">Это может занять до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="8a37e-304">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="8a37e-305">Пример: Настройка частного источника для семейства веб-сайтов для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-305">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<a name="ExamplePrivateOriginSiteCollection"> </a>

<span data-ttu-id="8a37e-306">Используйте командлет **Add-SPOTenantCdnOrigin** для определения семейства веб-сайтов в качестве частного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-306">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="8a37e-307">Пример:</span><span class="sxs-lookup"><span data-stu-id="8a37e-307">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="8a37e-308">Дополнительные сведения об этой команде и ее синтаксисе можно найти в статье [Add/SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-308">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="8a37e-309">После выполнения команды система синхронизирует конфигурацию в центре обработки данных.</span><span class="sxs-lookup"><span data-stu-id="8a37e-309">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="8a37e-310">Вы можете увидеть ожидающее сообщение о _конфигурации_ , которое ожидается, когда клиент SharePoint Online подключается к службе CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-310">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="8a37e-311">Это может занять до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="8a37e-311">This can take up to 15 minutes.</span></span>

### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="8a37e-312">Управление CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-312">Manage the Office 365 CDN</span></span>
<a name="CDNManage"> </a>

<span data-ttu-id="8a37e-313">После настройки сети CDN можно внести изменения в конфигурацию при обновлении содержимого или при необходимости изменения, как описано в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="8a37e-313">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="8a37e-314">Добавление, обновление и удаление ресурсов из сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-314">Add, update, or remove assets from the Office 365 CDN</span></span>
<a name="Office365CDNforSPOaddremoveasset"> </a>

<span data-ttu-id="8a37e-315">После завершения настройки вы можете добавить новые ресурсы, а также обновлять или удалять существующие ресурсы в любое время.</span><span class="sxs-lookup"><span data-stu-id="8a37e-315">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="8a37e-316">Внесите изменения в ресурсы в папке или библиотеке SharePoint, которую вы определили в качестве источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-316">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="8a37e-317">Если вы добавите новый ресурс, он будет доступен в CDN немедленно.</span><span class="sxs-lookup"><span data-stu-id="8a37e-317">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="8a37e-318">Тем не менее, если вы обновите актив, новая копия будет распространена и станет доступной в сети CDN до 15 минут.</span><span class="sxs-lookup"><span data-stu-id="8a37e-318">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="8a37e-319">Если необходимо извлечь расположение источника, можно использовать командлет **Get – SPOTenantCdnOrigins** .</span><span class="sxs-lookup"><span data-stu-id="8a37e-319">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="8a37e-320">Сведения о том, как использовать этот командлет, можно найти в статье [Get – SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-320">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="8a37e-321">Удаление источника из сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-321">Remove an origin from the Office 365 CDN</span></span>
<a name="Office365CDNforSPORemoveOrigin"> </a>

<span data-ttu-id="8a37e-322">Вы можете запретить доступ к папке или библиотеке SharePoint, идентифицированным в качестве источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-322">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="8a37e-323">Для этого используйте командлет reMove **– SPOTenantCdnOrigin** .</span><span class="sxs-lookup"><span data-stu-id="8a37e-323">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="8a37e-324">Сведения о том, как использовать этот командлет, можно найти в статье [Remove – SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-324">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="8a37e-325">Изменение источника в сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-325">Modify an origin in the Office 365 CDN</span></span>
<a name="Office365CDNforSPORemoveOrigin"> </a>

<span data-ttu-id="8a37e-326">Вы не можете изменить созданный вами источник.</span><span class="sxs-lookup"><span data-stu-id="8a37e-326">You cannot modify an origin you've created.</span></span> <span data-ttu-id="8a37e-327">Вместо этого удалите источник, а затем добавьте новый.</span><span class="sxs-lookup"><span data-stu-id="8a37e-327">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="8a37e-328">Для получения дополнительных сведений обратитесь [к разделу Удаление источника из сети CDN Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) и [Добавление источника для ресурсов](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="8a37e-328">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="8a37e-329">Отключение сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-329">Disable the Office 365 CDN</span></span>
<a name="Office365CDNforSPODisable"> </a>

<span data-ttu-id="8a37e-330">Используйте командлет **Set – SPOTenantCdnEnabled** для отключения сети CDN для Организации.</span><span class="sxs-lookup"><span data-stu-id="8a37e-330">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="8a37e-331">Если для сети CDN включены как общедоступные, так и частные источники, необходимо дважды выполнить командлет, как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="8a37e-331">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="8a37e-332">Чтобы отключить использование общедоступных источников в сети CDN, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-332">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="8a37e-333">Чтобы отключить использование частных источников в сети CDN, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-333">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="8a37e-334">Дополнительные сведения об этом командлете приведены в разделе [Set – SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a37e-334">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="8a37e-335">Установка и настройка сети CDN Office 365 с помощью интерфейса командной строки Office 365:</span><span class="sxs-lookup"><span data-stu-id="8a37e-335">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>
<a name="CDNSetupinCLI"> </a>

<span data-ttu-id="8a37e-336">Процедуры, описанные в этом разделе, требуют установки [Office 365 CLI](https://aka.ms/o365cli).</span><span class="sxs-lookup"><span data-stu-id="8a37e-336">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="8a37e-337">Затем подключитесь к клиенту SharePoint Online с помощью команды [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/).</span><span class="sxs-lookup"><span data-stu-id="8a37e-337">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="8a37e-338">Выполните указанные ниже действия, чтобы настроить и настроить сеть CDN для размещения ресурсов в SharePoint Online с помощью интерфейса CLI для Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a37e-338">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="8a37e-339">Включение сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-339">Enable the Office 365 CDN</span></span>

<span data-ttu-id="8a37e-340">Вы можете управлять состоянием сети CDN Office 365 в клиенте с помощью команды [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/).</span><span class="sxs-lookup"><span data-stu-id="8a37e-340">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="8a37e-341">Чтобы включить в клиенте общедоступную сеть CDN Office 365, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-341">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="8a37e-342">Чтобы включить Office 365 для SharePoint CDN, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8a37e-342">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="8a37e-343">Просмотр текущего состояния сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-343">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="8a37e-344">Чтобы проверить, включена или отключена ли определенная сеть CDN для Office 365, используйте команду [SPO CDN Get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) .</span><span class="sxs-lookup"><span data-stu-id="8a37e-344">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="8a37e-345">Чтобы проверить, включена ли общедоступная сеть CDN Office 365, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-345">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="8a37e-346">Просмотр источников сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-346">View the Office 365 CDN origins</span></span>

<span data-ttu-id="8a37e-347">Чтобы просмотреть список настроенных в данный момент общедоступных источников CDN Office 365, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-347">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="8a37e-348">Для получения сведений об источниках, подготовленных по умолчанию при включении сети CDN Office 365, просмотрите [источники CDN по умолчанию](use-office-365-cdn-with-spo.md#default-cdn-origins) .</span><span class="sxs-lookup"><span data-stu-id="8a37e-348">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="8a37e-349">Добавление источника CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-349">Add an Office 365 CDN origin</span></span>

> [!NOTE]
> <span data-ttu-id="8a37e-350">Никогда не следует помещать ресурсы, которые считаются конфиденциальными в Организации, в библиотеке документов SharePoint, настроенной в качестве общедоступного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-350">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="8a37e-351">Чтобы определить источник CDN, используйте команду [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/).</span><span class="sxs-lookup"><span data-stu-id="8a37e-351">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="8a37e-352">Вы можете определить несколько источников.</span><span class="sxs-lookup"><span data-stu-id="8a37e-352">You can define multiple origins.</span></span> <span data-ttu-id="8a37e-353">Источник — это URL-адрес, указывающий на библиотеку или папку в SharePoint, содержащую ресурсы, которые требуется размещать в сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-353">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="8a37e-354">`path` — это путь к папке, содержащей ресурсы.</span><span class="sxs-lookup"><span data-stu-id="8a37e-354">Where `path` is the path to the folder that contains the assets.</span></span> <span data-ttu-id="8a37e-355">Помимо относительных путей, можно использовать подстановочные знаки.</span><span class="sxs-lookup"><span data-stu-id="8a37e-355">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="8a37e-356">Чтобы включить все ресурсы в **коллекцию главных страниц** для всех сайтов в качестве общедоступного источника, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8a37e-356">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="8a37e-357">Чтобы настроить частный источник для определенного семейства веб-сайтов, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8a37e-357">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="8a37e-358">После добавления источника CDN может понадобиться до 15 минут, чтобы получить файлы через службу CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-358">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="8a37e-359">Вы можете проверить, включен ли тот или иной источник, с помощью команды [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/).</span><span class="sxs-lookup"><span data-stu-id="8a37e-359">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="8a37e-360">Удаление источника CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-360">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="8a37e-361">Чтобы удалить источник CDN для указанного типа CDN, используйте команду [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/).</span><span class="sxs-lookup"><span data-stu-id="8a37e-361">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="8a37e-362">Чтобы удалить общедоступный источник из конфигурации CDN, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8a37e-362">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="8a37e-363">Удаление источника CDN не влияет на файлы, хранящиеся в библиотеке документов, соответствующей этому источнику.</span><span class="sxs-lookup"><span data-stu-id="8a37e-363">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="8a37e-364">Если эти ресурсы упоминаются с помощью URL-адреса SharePoint, SharePoint автоматически переключится обратно на исходный URL-адрес, указывающий на библиотеку документов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-364">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="8a37e-365">Тем не менее, если у вас есть ссылки на ресурсы с помощью URL-адреса общедоступной сети CDN, то удаление источника приведет к разрыву связи и потребуется вручную изменить их.</span><span class="sxs-lookup"><span data-stu-id="8a37e-365">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="8a37e-366">Изменение источника CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-366">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="8a37e-367">Изменить имеющийся источник CDN невозможно.</span><span class="sxs-lookup"><span data-stu-id="8a37e-367">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="8a37e-368">Вместо этого следует удалить определенный ранее источник CDN с помощью команды `spo cdn origin remove` и добавить новый с помощью команды `spo cdn origin add`.</span><span class="sxs-lookup"><span data-stu-id="8a37e-368">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="8a37e-369">Изменение типов файлов, включаемых в CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-369">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="8a37e-370">По умолчанию для сети CDN включены следующие типы файлов: _CSS, EOT, GIF, ICO, JPEG, JPG, JS, MAP, PNG, SVG, TTF и WOFF_.</span><span class="sxs-lookup"><span data-stu-id="8a37e-370">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="8a37e-371">Если требуется включить в сеть CDN дополнительные типы файлов, вы можете изменить конфигурацию CDN с помощью команды [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).</span><span class="sxs-lookup"><span data-stu-id="8a37e-371">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="8a37e-372">При изменении списка типов файлов перезаписывается текущий список.</span><span class="sxs-lookup"><span data-stu-id="8a37e-372">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="8a37e-373">Если требуется включить дополнительные типы файлов, сперва используйте команду [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/), чтобы узнать, какие типы файлов настроены в текущий момент.</span><span class="sxs-lookup"><span data-stu-id="8a37e-373">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="8a37e-374">Чтобы добавить тип файла _JSON_ в список по умолчанию типов файлов, включенных в общедоступНУЮ сеть CDN, выполните:</span><span class="sxs-lookup"><span data-stu-id="8a37e-374">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="8a37e-375">Изменение списка классификаций сайтов, которые требуется исключить из сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-375">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="8a37e-376">Чтобы исключить классификации сайтов, которые не должны быть доступны в сети CDN, используйте команду [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).</span><span class="sxs-lookup"><span data-stu-id="8a37e-376">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="8a37e-377">По умолчанию не исключаются никакие классификации сайтов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-377">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="8a37e-378">При изменении списка исключаемых классификаций сайтов перезаписывается текущий список.</span><span class="sxs-lookup"><span data-stu-id="8a37e-378">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="8a37e-379">Если требуется исключить дополнительные классификации сайтов, сперва используйте команду [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/), чтобы узнать, какие классификации настроены в текущий момент.</span><span class="sxs-lookup"><span data-stu-id="8a37e-379">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="8a37e-380">Чтобы исключить сайты, классифицированные как _HBI_ , из общедоступНОЙ сети CDN, выполните</span><span class="sxs-lookup"><span data-stu-id="8a37e-380">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="8a37e-381">Отключение сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-381">Disable the Office 365 CDN</span></span>

<span data-ttu-id="8a37e-382">Чтобы отключить сеть CDN Office 365, используйте команду `spo cdn set`. Пример:</span><span class="sxs-lookup"><span data-stu-id="8a37e-382">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a><span data-ttu-id="8a37e-383">Использование ресурсов CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-383">Using your CDN assets</span></span>

<span data-ttu-id="8a37e-384">Теперь, когда вы включили CDN и настроенные источники и политики, вы можете приступить к использованию ресурсов CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-384">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="8a37e-385">В этом разделе вы узнаете, как использовать URL-адреса CDN в страницах и контенте SharePoint, чтобы SharePoint перенаправлял запросы ресурсов в общедоступных и частных источниках сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-385">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

- [<span data-ttu-id="8a37e-386">Обновление ссылок на ресурсы CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-386">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [<span data-ttu-id="8a37e-387">Использование ресурсов в общедоступных источниках</span><span class="sxs-lookup"><span data-stu-id="8a37e-387">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [<span data-ttu-id="8a37e-388">Использование ресурсов в частных источниках</span><span class="sxs-lookup"><span data-stu-id="8a37e-388">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="8a37e-389">Сведения о том, как использовать сеть CDN для размещения клиентских веб-частей, можно найти в разделе [Host The Client Web Part of Office 365 CDN (Hello World, часть 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span><span class="sxs-lookup"><span data-stu-id="8a37e-389">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="8a37e-390">Обновление ссылок на ресурсы CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-390">Updating links to CDN assets</span></span>

<span data-ttu-id="8a37e-391">Чтобы использовать ресурсы, добавленные в источник, просто обновите ссылки на исходный файл, указав путь к файлу в источнике.</span><span class="sxs-lookup"><span data-stu-id="8a37e-391">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

- <span data-ttu-id="8a37e-392">ОтРедактируйте страницу или контент, содержащие ссылки на ресурсы, добавленные в источник.</span><span class="sxs-lookup"><span data-stu-id="8a37e-392">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="8a37e-393">Вы также можете использовать один из следующих методов для глобального поиска и замены ссылок на сайте ввод сайта или семейства веб-сайтов, если необходимо обновить ссылку на данный ресурс везде, где он отображается.</span><span class="sxs-lookup"><span data-stu-id="8a37e-393">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
- <span data-ttu-id="8a37e-394">Для каждой ссылки на ресурс в источнике Замените путь на путь к файлу в источнике CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-394">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="8a37e-395">Можно использовать относительные пути.</span><span class="sxs-lookup"><span data-stu-id="8a37e-395">You can use relative paths.</span></span>
- <span data-ttu-id="8a37e-396">Сохраните страницу или контент.</span><span class="sxs-lookup"><span data-stu-id="8a37e-396">Save the page or content.</span></span>

<span data-ttu-id="8a37e-397">Например, рассмотрим изображение _/Сите/ситеассетс/имажес/имаже.ПНГ_, скопированное в папку библиотеки документов _/Сите/кдн_оригинс/публик/_.</span><span class="sxs-lookup"><span data-stu-id="8a37e-397">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="8a37e-398">Чтобы использовать ресурс CDN, замените исходный путь на путь к расположению файла изображения, указав путь к источнику, чтобы сделать новый URL-адрес _/Сите/кдн_оригинс/публик/имаже.ПНГ_.</span><span class="sxs-lookup"><span data-stu-id="8a37e-398">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="8a37e-399">Если вы хотите использовать полный URL-адрес для ресурса вместо относительного пути, создайте ссылку следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8a37e-399">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="8a37e-400">Как правило, не следует жестко кодировать URL-адреса непосредственно для ресурсов в сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-400">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="8a37e-401">Однако при необходимости можно вручную создавать URL-адреса для ресурсов в общедоступных источниках.</span><span class="sxs-lookup"><span data-stu-id="8a37e-401">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="8a37e-402">Дополнительные сведения см. в статье [URL-адреса CDN хардкодинг для общедоступных ресурсов](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span><span class="sxs-lookup"><span data-stu-id="8a37e-402">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="8a37e-403">Чтобы узнать, как проверить, что ресурсы обслуживаются из сети CDN, посмотрите, [как подтвердить, что активы обслуживаются в сети CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) в разделе Устранение неполадок в разделе [CDN Office 365](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="8a37e-403">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="8a37e-404">Использование ресурсов в общедоступных источниках</span><span class="sxs-lookup"><span data-stu-id="8a37e-404">Using assets in public origins</span></span>

<span data-ttu-id="8a37e-405">**Функция публикации** в SharePoint Online автоматически перезаписывает URL-адреса ресурсов, хранящихся в общедоступных источниках, в их ЭКВИВАЛЕНТы CDN, чтобы ресурсы направляются из службы CDN, а не из SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8a37e-405">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="8a37e-406">Если ваш источник находится на сайте с включенным компонентом публикации, а ресурсы, которые вы хотите отгрузить в CDN, находятся в одной из следующих категорий, SharePoint автоматически переписывает URL-адреса для ресурсов в источнике при условии, что актив не был исключен из сети CDN.  политику.</span><span class="sxs-lookup"><span data-stu-id="8a37e-406">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="8a37e-407">Ниже представлен обзор ссылок, которые автоматически заменяет функция публикации в SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8a37e-407">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

- <span data-ttu-id="8a37e-408">URL-адреса IMG-, LINK- и CSS-файлов в HTML-откликах классической страницы публикации.</span><span class="sxs-lookup"><span data-stu-id="8a37e-408">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  - <span data-ttu-id="8a37e-409">Это относится и к изображениям, добавленным авторами в HTML-содержимом страницы.</span><span class="sxs-lookup"><span data-stu-id="8a37e-409">This includes images added by authors within the HTML content of a page</span></span>
- <span data-ttu-id="8a37e-410">URL-адреса изображений в веб-части "Слайд-шоу библиотеки рисунков".</span><span class="sxs-lookup"><span data-stu-id="8a37e-410">Picture Library SlideShow webpart image URLs</span></span>
- <span data-ttu-id="8a37e-411">Поля изображений в результатах работы REST API SPList (RenderListDataAsStream).</span><span class="sxs-lookup"><span data-stu-id="8a37e-411">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  - <span data-ttu-id="8a37e-412">Используйте новое свойство _имажефиелдстотриревритетокднурлс_ , чтобы предоставить список полей, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="8a37e-412">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  - <span data-ttu-id="8a37e-413">Поддерживает поля гиперссылок и поля PublishingImage</span><span class="sxs-lookup"><span data-stu-id="8a37e-413">Supports hyperlink fields and PublishingImage fields</span></span>
- <span data-ttu-id="8a37e-414">Представления изображений SharePoint</span><span class="sxs-lookup"><span data-stu-id="8a37e-414">SharePoint image renditions</span></span>

<span data-ttu-id="8a37e-415">На следующей схеме показан рабочий процесс, когда SharePoint получает запрос на страницу, содержащую ресурсы из общедоступного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-415">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="8a37e-416">![Схема рабочего процесса: получение ресурсов CDN Office 365 из общедоступного источника] (media/O365-CDN/o365-cdn-public-steps-transparent.svg "Рабочий процесс: получение ресурсов CDN Office 365 из общедоступного источника")</span><span class="sxs-lookup"><span data-stu-id="8a37e-416">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="8a37e-417">Если вы хотите отключить автоматическое переопределение определенных URL-адресов на странице, можно извлечь страницу и добавить параметр строки запроса **_км_ноауторевритес = true** в конец каждой из ссылок, которую требуется отключить.</span><span class="sxs-lookup"><span data-stu-id="8a37e-417">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="8a37e-418">URL-адреса CDN Хардкодинг для общедоступных активов</span><span class="sxs-lookup"><span data-stu-id="8a37e-418">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="8a37e-419">Если функция _публикации_ не включена для общедоступного источника, или актив не является одним из типов связей, поддерживаемых функцией автоматического перезаписи службы CDN, можно вручную создать URL-адреса для расположения в сети CDN и использовать эти URL-адреса в контенте.</span><span class="sxs-lookup"><span data-stu-id="8a37e-419">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="8a37e-420">Невозможно жестко кодировать URL-адреса CDN в ресурсы в частном источнике, так как необходимый маркер доступа, который образует последний раздел URL-адреса, создается во время запроса ресурса.</span><span class="sxs-lookup"><span data-stu-id="8a37e-420">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="8a37e-421">Для ресурсов общедоступной сети CDN формат URL-адреса будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8a37e-421">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="8a37e-422">Замените **тенансостнаме** на имя вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="8a37e-422">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="8a37e-423">Пример:</span><span class="sxs-lookup"><span data-stu-id="8a37e-423">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="8a37e-424">Использование ресурсов в частных источниках</span><span class="sxs-lookup"><span data-stu-id="8a37e-424">Using assets in private origins</span></span>

<span data-ttu-id="8a37e-425">Для использования ресурсов в частных источниках не требуется дополнительная настройка.</span><span class="sxs-lookup"><span data-stu-id="8a37e-425">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="8a37e-426">SharePoint Online автоматически перезаписывает URL-адреса для ресурсов в частных источниках, поэтому запросы для этих ресурсов будут всегда обслуживаться из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-426">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="8a37e-427">Вы не можете вручную создавать URL-адреса для ресурсов CDN в частных источниках, так как эти URL-адреса содержат маркеры, которые должны автоматически создаваться SharePoint Online при запросе ресурса.</span><span class="sxs-lookup"><span data-stu-id="8a37e-427">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="8a37e-428">Доступ к ресурсам в частных источниках защищен динамически создаваемыми маркерами на основе разрешений пользователя на происхождение, а также предостережений, описанных в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="8a37e-428">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="8a37e-429">Пользователи должны иметь по крайней мере доступ на **Чтение** к источникАМ сети CDN для отображения контента.</span><span class="sxs-lookup"><span data-stu-id="8a37e-429">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="8a37e-430">На следующей схеме показан рабочий процесс, когда SharePoint получает запрос на страницу, содержащую ресурсы из частного источника.</span><span class="sxs-lookup"><span data-stu-id="8a37e-430">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="8a37e-431">![Схема рабочего процесса: получение ресурсов CDN Office 365 из частного источника] (media/O365-CDN/o365-cdn-private-steps-transparent.svg "Рабочий процесс: получение ресурсов CDN Office 365 из частного источника")</span><span class="sxs-lookup"><span data-stu-id="8a37e-431">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="8a37e-432">Авторизация на основе маркеров в частных источниках</span><span class="sxs-lookup"><span data-stu-id="8a37e-432">Token-based authorization in private origins</span></span>

<span data-ttu-id="8a37e-433">Доступ к ресурсам в частных источниках в сети CDN Office 365 предоставляется маркерами, созданными SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-433">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="8a37e-434">Пользователи, которые уже имеют разрешение на доступ к папке или библиотеке, назначенным источником, автоматически получают маркеры, позволяющие пользователю получить доступ к файлу на основе их уровня разрешений.</span><span class="sxs-lookup"><span data-stu-id="8a37e-434">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="8a37e-435">Эти маркеры доступа действительны в течение 30 – 90 минут после их создания для предотвращения атак с повторением маркеров.</span><span class="sxs-lookup"><span data-stu-id="8a37e-435">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="8a37e-436">После создания маркера доступа SharePoint Online возвращает пользовательский URI для клиента, содержащего два параметра авторизации _EAT_ (маркер авторизации пограничного сервера) и _ОАТ_ (маркер авторизации источника).</span><span class="sxs-lookup"><span data-stu-id="8a37e-436">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="8a37e-437">Структура каждого маркера __лт_'експиратион время в эпоху времени Формат'_гт____лт_'секуре сигнатуре'_гт__.</span><span class="sxs-lookup"><span data-stu-id="8a37e-437">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="8a37e-438">Пример:</span><span class="sxs-lookup"><span data-stu-id="8a37e-438">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="8a37e-439">Любой пользователь, имеющий право на получение маркера, может получить доступ к ресурсу в сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-439">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="8a37e-440">Однако URL-адреса, содержащие эти маркеры доступа, разделяются только по ПРОТОКОЛу HTTPS, поэтому до истечения срока действия маркера пользователь не будет иметь доступ к URL-АДРЕСу явным образом, он будет недоступен для неавторизованных пользователей.</span><span class="sxs-lookup"><span data-stu-id="8a37e-440">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="8a37e-441">Разрешения на уровне элементов не поддерживаются для ресурсов в частных источниках</span><span class="sxs-lookup"><span data-stu-id="8a37e-441">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="8a37e-442">Важно отметить, что SharePoint Online не поддерживает разрешения на уровне элементов для ресурсов в частных источниках.</span><span class="sxs-lookup"><span data-stu-id="8a37e-442">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="8a37e-443">Например, для файла, расположенного в `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, пользователи имеют эффективный доступ к файлу с учетом следующих условий:</span><span class="sxs-lookup"><span data-stu-id="8a37e-443">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="8a37e-444">Пользователь</span><span class="sxs-lookup"><span data-stu-id="8a37e-444">User</span></span>  |<span data-ttu-id="8a37e-445">Разрешения</span><span class="sxs-lookup"><span data-stu-id="8a37e-445">Permissions</span></span>  |<span data-ttu-id="8a37e-446">Эффективный доступ</span><span class="sxs-lookup"><span data-stu-id="8a37e-446">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="8a37e-447">Пользователь 1</span><span class="sxs-lookup"><span data-stu-id="8a37e-447">User 1</span></span>     |<span data-ttu-id="8a37e-448">Имеет доступ к Folder1</span><span class="sxs-lookup"><span data-stu-id="8a37e-448">Has access to folder1</span></span>         |<span data-ttu-id="8a37e-449">Может получить доступ к image1. jpg из сети CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-449">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="8a37e-450">Пользователь 2</span><span class="sxs-lookup"><span data-stu-id="8a37e-450">User 2</span></span>     |<span data-ttu-id="8a37e-451">Не имеет доступа к Folder1</span><span class="sxs-lookup"><span data-stu-id="8a37e-451">Does not have access to folder1</span></span>         |<span data-ttu-id="8a37e-452">Не удается получить доступ к image1. jpg из сети CDN</span><span class="sxs-lookup"><span data-stu-id="8a37e-452">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="8a37e-453">Пользователь 3</span><span class="sxs-lookup"><span data-stu-id="8a37e-453">User 3</span></span>     |<span data-ttu-id="8a37e-454">Не имеет доступа к Folder1, но ему предоставлено явное разрешение на доступ к image1. jpg в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-454">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="8a37e-455">Может получать доступ к ресурсу image1. jpg непосредственно из SharePoint Online, но не из сети CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-455">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="8a37e-456">Пользователь 4</span><span class="sxs-lookup"><span data-stu-id="8a37e-456">User 4</span></span>     |<span data-ttu-id="8a37e-457">Имеет доступ к Folder1, но ему явно отказано в доступе к image1. jpg в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-457">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="8a37e-458">Не удается получить доступ к ресурсу из SharePoint Online, но он может получить доступ к ресурсу из CDN, несмотря на запрет доступа к файлу в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-458">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="8a37e-459">Устранение неполадок в сети CDN Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-459">Troubleshooting the Office 365 CDN</span></span>
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="8a37e-460">Как убедиться, что активы обслуживаются в сети CDN?</span><span class="sxs-lookup"><span data-stu-id="8a37e-460">How do I confirm that assets are being served by the CDN?</span></span>
<a name="CDNConfirm"> </a>

<span data-ttu-id="8a37e-461">Когда вы добавили ссылки на ресурсы CDN на страницу, вы можете убедиться, что актив обслуживается из сети CDN, перейдя на страницу, щелкнув изображение правой кнопкой мыши после того, как оно отрисовывается и просматривает URL-адрес изображения.</span><span class="sxs-lookup"><span data-stu-id="8a37e-461">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="8a37e-462">Кроме того, с помощью средств разработчика браузера можно просматривать URL-адрес каждого ресурса на странице или использовать средство трассировки сети стороннего производителя.</span><span class="sxs-lookup"><span data-stu-id="8a37e-462">You can also use your browser's developer tools to view the URL for each asset on a page, or use a 3rd party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="8a37e-463">Если вы используете сетевое средство, например Fiddler, для тестирования ресурсов за предельным отображением ресурса на странице SharePoint, необходимо вручную добавить заголовок источника ссылки "ссылка" `https://yourdomain.sharepoint.com`: в запрос GET, где URL-адрес — это корневой URL-адрес клиента SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-463">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="8a37e-464">Вы не можете проверить URL-адреса CDN непосредственно в веб-браузере, так как вам потребуется источник ссылки, поступающий из SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8a37e-464">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="8a37e-465">Тем не менее, если вы добавите URL-адрес ресурса CDN на страницу SharePoint, а затем открыли страницу в браузере, на странице появится ресурс CDN, отображаемый на странице.</span><span class="sxs-lookup"><span data-stu-id="8a37e-465">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="8a37e-466">Для получения дополнительных сведений об использовании средств разработчика в браузере Microsoft Edge обратитесь к разделу [Инструменты разработчика Microsoft Edge](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span><span class="sxs-lookup"><span data-stu-id="8a37e-466">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="8a37e-467">Почему ресурсы из нового источника недоступны?</span><span class="sxs-lookup"><span data-stu-id="8a37e-467">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="8a37e-468">Ресурсы в новых источниках сразу не будут доступны для использования, так как они занимают время для распространения в сети CDN и для загрузки активов из источника в хранилище CDN.</span><span class="sxs-lookup"><span data-stu-id="8a37e-468">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="8a37e-469">Время, необходимое для доступа к ресурсам в сети CDN, зависит от количества ресурсов и размера файлов.</span><span class="sxs-lookup"><span data-stu-id="8a37e-469">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="8a37e-470">Клиентская веб-часть или решение SharePoint Framework не работают</span><span class="sxs-lookup"><span data-stu-id="8a37e-470">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="8a37e-471">Когда вы включаете CDN Office 365 для общедоступных источников, служба CDN автоматически создает следующие начальные значения по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="8a37e-471">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

- <span data-ttu-id="8a37e-472">\*/МАСТЕРПАЖЕ</span><span class="sxs-lookup"><span data-stu-id="8a37e-472">\*/MASTERPAGE</span></span>
- <span data-ttu-id="8a37e-473">\* БИБЛИОТЕКА/STYLE LIBRARY</span><span class="sxs-lookup"><span data-stu-id="8a37e-473">\*/STYLE LIBRARY</span></span>
- <span data-ttu-id="8a37e-474">\*/КЛИЕНТСИДЕАССЕТС</span><span class="sxs-lookup"><span data-stu-id="8a37e-474">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="8a37e-475">Если источник \*/клиентсидеассетс отсутствует, решения SharePoint Framework завершатся неуспешно, и предупреждения или сообщения об ошибках не создаются.</span><span class="sxs-lookup"><span data-stu-id="8a37e-475">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="8a37e-476">Этот источник может отсутствовать из-за того, что для сети CDN включен параметр _-нодефаулторигинс_ , для которого задано значение **$true**или удалено удаление источника вручную.</span><span class="sxs-lookup"><span data-stu-id="8a37e-476">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="8a37e-477">Вы можете проверить, присутствует ли источник \*/КЛИЕНТСИДЕАССЕТС с помощью следующей команды PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8a37e-477">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="8a37e-478">Вы также можете проверить наличие Office 365 CLI:</span><span class="sxs-lookup"><span data-stu-id="8a37e-478">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="8a37e-479">Чтобы добавить источник в PowerShell, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8a37e-479">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="8a37e-480">Чтобы добавить источник в Office 365 CLI:</span><span class="sxs-lookup"><span data-stu-id="8a37e-480">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="8a37e-481">Какие модули PowerShell и оболочки CLI необходимо использовать для работы с CDN Office 365?</span><span class="sxs-lookup"><span data-stu-id="8a37e-481">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="8a37e-482">Вы можете работать с CDN Office 365 с помощью модуля PowerShell **SharePoint Online Management Shell** или **Office 365 CLI**.</span><span class="sxs-lookup"><span data-stu-id="8a37e-482">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

- [<span data-ttu-id="8a37e-483">Начало работы с командной консолью SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8a37e-483">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [<span data-ttu-id="8a37e-484">Установка Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="8a37e-484">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="8a37e-485">См. также</span><span class="sxs-lookup"><span data-stu-id="8a37e-485">See also</span></span>

[<span data-ttu-id="8a37e-486">Сети доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="8a37e-486">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="8a37e-487">Планирование сети и настройка производительности для Office 365</span><span class="sxs-lookup"><span data-stu-id="8a37e-487">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

