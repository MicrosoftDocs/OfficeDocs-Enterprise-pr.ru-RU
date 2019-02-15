---
title: Поддержка нескольких регионов в OneDrive для Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Расширьте свою географию присутствия Office 365 с поддержкой нескольких регионов в OneDrive Online.
ms.openlocfilehash: f89bfe7cb9a287200591746dc6d22430cd6eed1b
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "30052993"
---
# <a name="multi-geo-capabilities-in-onedrive-in-office-365"></a><span data-ttu-id="4fdae-103">Поддержка нескольких регионов в OneDrive для Office 365</span><span class="sxs-lookup"><span data-stu-id="4fdae-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="4fdae-p101">Поддержка нескольких регионов в OneDrive Online позволяет организации развивать бизнес в нескольких географических регионах или странах, используя существующий клиент Office 365. Обратитесь в отдел по работе с клиентами Майкрософт, чтобы зарегистрировать свою международную компанию в OneDrive для бизнеса с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="4fdae-p101">With Multi-Geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="4fdae-106">Поддержка нескольких регионов в службе OneDrive позволяет подготавливать и хранить неактивные данные в выбранных вами регионах, а также предоставлять современные возможности для работы всем сотрудникам.</span><span class="sxs-lookup"><span data-stu-id="4fdae-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="4fdae-107">Вот какие преимущества дает поддержка нескольких регионов:</span><span class="sxs-lookup"><span data-stu-id="4fdae-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="4fdae-108">Работайте как одна глобальная организация с одним клиентом Office 365 на несколько регионов.</span><span class="sxs-lookup"><span data-stu-id="4fdae-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="4fdae-109">Обеспечьте соблюдение требований, создавая и размещая неактивные данные в определенном регионе.</span><span class="sxs-lookup"><span data-stu-id="4fdae-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="4fdae-110">Предоставьте удаленным сотрудникам те же современные возможности для работы, что и сотрудникам в центральном офисе.</span><span class="sxs-lookup"><span data-stu-id="4fdae-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="4fdae-111">Позвольте пользователям перемещаться из одного географического региона в другой, не теряя доступ к контенту.</span><span class="sxs-lookup"><span data-stu-id="4fdae-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="4fdae-112">Подберите политики общего доступа для каждого региона и политики защиты от потери данных для каждого сайта.</span><span class="sxs-lookup"><span data-stu-id="4fdae-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="4fdae-113">Назначьте ответственных за обнаружение электронных данных для каждого региона и разрешите им управлять делами этого региона.</span><span class="sxs-lookup"><span data-stu-id="4fdae-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="4fdae-114">Выберите уникальные пространства имен URL (например, ContosoEUR.sharepoint.com) для дополнительных регионов.</span><span class="sxs-lookup"><span data-stu-id="4fdae-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="4fdae-115">Объедините региональные локальные данные в одном клиенте Office 365.</span><span class="sxs-lookup"><span data-stu-id="4fdae-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="4fdae-p102">В конфигурации с несколькими регионами клиент Office 365 состоит из центрального расположения (где изначально была подготовлена подписка на Office 365) и одного или нескольких удаленных регионов. Основная концепция поддержки нескольких регионов заключается в том, что один клиент охватывает несколько регионов. В клиенте с несколькими регионами информация о регионах, группах и пользователях обрабатывается в Azure Active Directory (AAD). Так как информация клиента обрабатывается централизованно и синхронизируется с каждым регионом, общий доступ и возможности в компании носят глобальный характер.</span><span class="sxs-lookup"><span data-stu-id="4fdae-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="4fdae-120">Видео: знакомство с Office 365 с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="4fdae-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="4fdae-121">Настройка поддержки нескольких регионов в три простых шага</span><span class="sxs-lookup"><span data-stu-id="4fdae-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="4fdae-122">Настроить поддержку нескольких регионов просто:</span><span class="sxs-lookup"><span data-stu-id="4fdae-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="4fdae-p103">Совместно с группой специалистов, занимающихся учетными записями, добавьте план обслуживания _с поддержкой нескольких регионов в Office 365_. Они помогут вам добавить необходимое количество лицензий.</span><span class="sxs-lookup"><span data-stu-id="4fdae-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="4fdae-125">Добавьте удаленные регионы.</span><span class="sxs-lookup"><span data-stu-id="4fdae-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="4fdae-126">Настройте учетные записи пользователей для соответствующего региона.</span><span class="sxs-lookup"><span data-stu-id="4fdae-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="4fdae-127">Состояние и доступность поддержки нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="4fdae-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="4fdae-128">В настоящее время поддержка нескольких регионов в OneDrive доступна в таких странах и регионах:</span><span class="sxs-lookup"><span data-stu-id="4fdae-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="4fdae-129">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="4fdae-129">Asia-Pacific</span></span>

- <span data-ttu-id="4fdae-130">Австралия</span><span class="sxs-lookup"><span data-stu-id="4fdae-130">Australia</span></span>

- <span data-ttu-id="4fdae-131">Канада</span><span class="sxs-lookup"><span data-stu-id="4fdae-131">Canada</span></span>

- <span data-ttu-id="4fdae-132">Европейский Союз (Европа, Ближний Восток и Африка)</span><span class="sxs-lookup"><span data-stu-id="4fdae-132">European Union (EMEA)</span></span>

- <span data-ttu-id="4fdae-133">Франция</span><span class="sxs-lookup"><span data-stu-id="4fdae-133">France</span></span>

- <span data-ttu-id="4fdae-134">Индия</span><span class="sxs-lookup"><span data-stu-id="4fdae-134">India</span></span>

- <span data-ttu-id="4fdae-135">Япония</span><span class="sxs-lookup"><span data-stu-id="4fdae-135">Japan</span></span>

- <span data-ttu-id="4fdae-136">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="4fdae-136">United Kingdom</span></span>

- <span data-ttu-id="4fdae-137">Соединенные Штаты (Северная Америка)</span><span class="sxs-lookup"><span data-stu-id="4fdae-137">United States (North America)</span></span>

- <span data-ttu-id="4fdae-138">Республика Корея</span><span class="sxs-lookup"><span data-stu-id="4fdae-138">Korea</span></span>

## <a name="getting-started"></a><span data-ttu-id="4fdae-139">Начало работы</span><span class="sxs-lookup"><span data-stu-id="4fdae-139">Getting started</span></span>

<span data-ttu-id="4fdae-p104">Чтобы начать работу с OneDrive для бизнеса с поддержкой нескольких регионов, [спланируйте среду](plan-for-multi-geo.md). Затем [узнайте об администрировании этой среды](administering-a-multi-geo-environment.md) и [особенностях взаимодействия с ней](multi-geo-user-experience.md). Когда вы будете готовы настроить OneDrive для бизнеса с поддержкой нескольких регионов, [настройте поддержку нескольких регионов в своем клиенте](multi-geo-tenant-configuration.md), а затем [переместите все сайты OneDrive в новые регионы](move-onedrive-between-geo-locations.md) и [настройте поиск](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="4fdae-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
