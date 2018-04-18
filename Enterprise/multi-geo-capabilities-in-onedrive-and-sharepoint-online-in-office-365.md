---
title: Поддержка нескольких регионов в OneDrive и SharePoint Online в Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Разверните узел состояние присутствия Office 365 для нескольких географических регионов с несколькими географически возможности в OneDrive и SharePoint Online.
ms.openlocfilehash: edcd8895c4a6e57ae1124ad15a9c5cc2b6bf94ca
ms.sourcegitcommit: 63e2844daa2863dddcd84819966a708c434e8580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="a8401-103">Поддержка нескольких регионов в OneDrive и SharePoint Online в Office 365</span><span class="sxs-lookup"><span data-stu-id="a8401-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="a8401-p101">С несколькими географически возможности в OneDrive и SharePoint Online организации могут расширить его присутствие Office 365 для нескольких географических областей и странах в рамках существующего клиента. Доступ к ваша группа учетной записи Майкрософт для подписки на вашей компании несколькими национальный OneDrive для бизнеса Multi-географически.</span><span class="sxs-lookup"><span data-stu-id="a8401-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="a8401-106">С несколькими OneDrive-географически, можно подготовить и хранения статических данных в географически местах, выбранные в соответствии с требованиями местонахождения данных и в то же время разблокировки вашей глобального развертывание современных работы для сотрудников.</span><span class="sxs-lookup"><span data-stu-id="a8401-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="a8401-107">Вот, как ферма с несколькими географически функции могут помочь вашей организации:</span><span class="sxs-lookup"><span data-stu-id="a8401-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="a8401-108">Работайте как одна глобальная организация с одним клиентом Office 365 на несколько регионов.</span><span class="sxs-lookup"><span data-stu-id="a8401-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="a8401-109">Обеспечьте соблюдение требований, создавая и размещая неактивные данные в определенном регионе.</span><span class="sxs-lookup"><span data-stu-id="a8401-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="a8401-110">Предоставьте удаленным сотрудникам те же современные возможности для работы, что и сотрудникам в центральном офисе.</span><span class="sxs-lookup"><span data-stu-id="a8401-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="a8401-111">Позвольте пользователям перемещаться из одного географического региона в другой, не теряя доступ к контенту.</span><span class="sxs-lookup"><span data-stu-id="a8401-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="a8401-112">Подберите политики общего доступа для каждого региона и политики защиты от потери данных для каждого сайта.</span><span class="sxs-lookup"><span data-stu-id="a8401-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="a8401-113">Назначьте ответственных за обнаружение электронных данных для каждого региона и разрешите им управлять делами этого региона.</span><span class="sxs-lookup"><span data-stu-id="a8401-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="a8401-114">Выберите уникальные пространства имен URL (например, ContosoEUR.sharepoint.com) для дополнительных регионов.</span><span class="sxs-lookup"><span data-stu-id="a8401-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="a8401-115">Объедините региональные локальные данные в одном клиенте Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8401-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="a8401-p102">В конфигурации с несколькими географически клиента Office 365 состоит из центрального расположения (также известной как расположение по умолчанию) и одно или несколько расположений географически вспомогательных. Основные концепции несколькими географически — это, что один клиент будет охватывающих один нескольких географического расположения. В географически несколькими клиента со сведениями о географического расположения, групп и сведений о пользователе, управляется в Azure Active Directory (AAD). Так как данные клиента создаются централизованно и синхронизируются в каждой географического расположения, общий доступ к и каждый раз, связанных с кем-либо вашей компании содержат сведения о глобальных.</span><span class="sxs-lookup"><span data-stu-id="a8401-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="a8401-120">Видео: Знакомство с Office 365 Multi географически</span><span class="sxs-lookup"><span data-stu-id="a8401-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="a8401-121">Настройка поддержки нескольких регионов в три простых шага</span><span class="sxs-lookup"><span data-stu-id="a8401-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="a8401-122">Настроить поддержку нескольких регионов просто:</span><span class="sxs-lookup"><span data-stu-id="a8401-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="a8401-p103">Работа с коллегами учетной записи для добавления план обслуживания _Несколькими географически возможности в Office 365_ . Они позволят добавить число лицензий.</span><span class="sxs-lookup"><span data-stu-id="a8401-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="a8401-125">Добавьте удаленные регионы.</span><span class="sxs-lookup"><span data-stu-id="a8401-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="a8401-126">Настройте учетные записи пользователей для соответствующего региона.</span><span class="sxs-lookup"><span data-stu-id="a8401-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="a8401-127">Состояние и доступность поддержки нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="a8401-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="a8401-128">В настоящее время поддержка нескольких регионов в OneDrive доступна в таких странах и регионах:</span><span class="sxs-lookup"><span data-stu-id="a8401-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="a8401-129">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="a8401-129">Asia-Pacific</span></span>
    
- <span data-ttu-id="a8401-130">Австралия</span><span class="sxs-lookup"><span data-stu-id="a8401-130">Australia</span></span>
    
- <span data-ttu-id="a8401-131">Канада</span><span class="sxs-lookup"><span data-stu-id="a8401-131">Canada</span></span>
    
- <span data-ttu-id="a8401-132">Европейский Союз (Европа, Ближний Восток и Африка)</span><span class="sxs-lookup"><span data-stu-id="a8401-132">European Union (EMEA)</span></span>
    
- <span data-ttu-id="a8401-133">Япония</span><span class="sxs-lookup"><span data-stu-id="a8401-133">Japan</span></span>
    
- <span data-ttu-id="a8401-134">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="a8401-134">United Kingdom</span></span>
    
- <span data-ttu-id="a8401-135">США (Северная Америка)</span><span class="sxs-lookup"><span data-stu-id="a8401-135">United States (North America)</span></span>
    
- <span data-ttu-id="a8401-136">Корея</span><span class="sxs-lookup"><span data-stu-id="a8401-136">Korea</span></span>
      
<span data-ttu-id="a8401-137">Скоро:</span><span class="sxs-lookup"><span data-stu-id="a8401-137">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="a8401-138">Франция</span><span class="sxs-lookup"><span data-stu-id="a8401-138">France</span></span>
- <span data-ttu-id="a8401-139">Индия</span><span class="sxs-lookup"><span data-stu-id="a8401-139">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="a8401-140">Начало работы</span><span class="sxs-lookup"><span data-stu-id="a8401-140">Getting started</span></span>

<span data-ttu-id="a8401-p104">Чтобы начать работу со службой OneDrive для бизнеса Multi-географически, первым делом для [планирования OneDrive for Business Multi-географически среды](plan-for-multi-geo.md). Далее, [сведения об администрировании несколькими географически среды](administering-a-multi-geo-environment.md) и [как пользователи смогут работать в среде несколькими географически](multi-geo-user-experience.md). Если все готово для установки OneDrive для бизнеса несколькими-географически, [Настройка вашего клиента для нескольких географически](multi-geo-tenant-configuration.md), затем [переместить всех существующих сайтов OneDrive их новые географического расположения](move-onedrive-between-geo-locations.md) и [Настройка поиска](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="a8401-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
