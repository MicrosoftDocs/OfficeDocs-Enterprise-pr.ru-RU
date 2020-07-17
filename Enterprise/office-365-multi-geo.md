---
title: Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Расширьте присутствие Microsoft 365 до нескольких регионов с помощью Microsoft 365 Multi-Geo.
ms.openlocfilehash: a49ba9b9b5109972a6b0a631d34d14acb189f484
ms.sourcegitcommit: 6b12e3ab76809d5632923def7ee367cd48ef3ccc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/13/2020
ms.locfileid: "45117281"
---
# <a name="microsoft-365-multi-geo"></a><span data-ttu-id="190a9-103">Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="190a9-103">Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="190a9-104">С помощью Microsoft 365 Multi-Geo организация может расширить присутствие Microsoft 365 до нескольких географических регионов или стран в существующем клиенте.</span><span class="sxs-lookup"><span data-stu-id="190a9-104">With Microsoft 365 Multi-Geo, your organization can expand its Microsoft 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="190a9-105">Обратитесь в службу поддержки учетных записей Майкрософт, чтобы зарегистрировать транснациональную компанию в Microsoft 365 Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="190a9-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Microsoft 365 Multi-Geo.</span></span>
  
<span data-ttu-id="190a9-106">Использование Microsoft 365 Multi-Geo позволяет подготавливать и хранить неактивные данные в выбранных вами географических расположениях в соответствии с требованиями к месту расположения данных, а также предоставлять современные возможности для работы всем сотрудникам.</span><span class="sxs-lookup"><span data-stu-id="190a9-106">With Microsoft 365 Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-microsoft-365-multi-geo"></a><span data-ttu-id="190a9-107">Видео. Знакомство с Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="190a9-107">Video: Introducing Microsoft 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="190a9-108">В среде с поддержкой нескольких регионов клиент Microsoft 365 включает центральное расположение (где изначально подготавливается подписка на Microsoft 365) и одно или несколько вспомогательных расположений.</span><span class="sxs-lookup"><span data-stu-id="190a9-108">In a Multi-Geo environment, your Microsoft 365 tenant consists of a central location (where your Microsoft 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="190a9-109">В клиенте с поддержкой нескольких регионов управление сведениями о географических расположениях, группах и пользователях выполняется в Azure Active Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="190a9-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="190a9-110">Так как информация клиента обрабатывается централизованно и синхронизируется с каждым регионом, общий доступ и возможности в компании носят глобальный характер.</span><span class="sxs-lookup"><span data-stu-id="190a9-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![Снимок экрана: карта нескольких регионов в Центре администрирования SharePoint](media/multi-geo-world-map.png)

<span data-ttu-id="190a9-112">Обратите внимание, что Microsoft 365 Multi-Geo не предназначен для повышения производительности. Он предназначен для соблюдения требований к месту расположения данных.</span><span class="sxs-lookup"><span data-stu-id="190a9-112">Note that Microsoft 365 Multi-Geo is not designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="190a9-113">Сведения о повышении производительности для Microsoft 365 см. в статье [Планирование сети и настройка производительности для Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848). Вы также можете связаться с группой поддержки.</span><span class="sxs-lookup"><span data-stu-id="190a9-113">For information about performance optimization for Microsoft 365, see [Network planning and performance tuning for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="190a9-114">Терминология</span><span class="sxs-lookup"><span data-stu-id="190a9-114">Terminology</span></span>

<span data-ttu-id="190a9-115">Ниже приводятся основные термины, используемые при описании Microsoft 365 Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="190a9-115">Here are the key terms used in describing Microsoft 365 Multi-Geo:</span></span>

- <span data-ttu-id="190a9-116">**Центральное расположение** — географическое расположение, в котором изначально подготовлен клиент.</span><span class="sxs-lookup"><span data-stu-id="190a9-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="190a9-117">**Администратор геообъекта** — администратор, который может управлять одним или несколькими периферийными расположениями.</span><span class="sxs-lookup"><span data-stu-id="190a9-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="190a9-118">**Код региона** — код из трех букв для определенного географического расположения.</span><span class="sxs-lookup"><span data-stu-id="190a9-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="190a9-119">**Географическое расположение** — регион, который можно использовать в клиенте с поддержкой нескольких регионов для размещения данных, включая почтовые ящики Exchange, а также сайты OneDrive и SharePoint.</span><span class="sxs-lookup"><span data-stu-id="190a9-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="190a9-120">**Предпочтительное расположение данных (PDL)** — свойство пользователя, устанавливаемое администратором, которое указывает географическое расположение, где следует подготовить почтовый ящик Exchange и хранилище OneDrive пользователей.</span><span class="sxs-lookup"><span data-stu-id="190a9-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="190a9-121">PDL также определяет, где подготовлены сайты SharePoint, созданные пользователем.</span><span class="sxs-lookup"><span data-stu-id="190a9-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="190a9-122">**Вспомогательное расположение** — географическое расположение, где учитывающие регион рабочие нагрузки Microsoft 365 (SharePoint, OneDrive и Exchange) включены в клиенте с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="190a9-122">**Satellite location** – The geo locations where the geo-aware Microsoft 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="190a9-123">**Клиент** — представление организации в Microsoft 365, которое имеет, как правило, один или несколько связанных с ним доменов (например, contoso.com).</span><span class="sxs-lookup"><span data-stu-id="190a9-123">**Tenant** – An organization's representation in Microsoft 365 which typically has one or more domains associated with it (for example, contoso.com).</span></span>

## <a name="licensing"></a><span data-ttu-id="190a9-124">Лицензирование</span><span class="sxs-lookup"><span data-stu-id="190a9-124">Licensing</span></span>

<span data-ttu-id="190a9-125">Microsoft 365 с поддержкой нескольких регионов доступен как надстройка для планов подписки Microsoft 365 для клиентов EA с не менее чем 250 рабочих мест Microsoft 365 в клиенте и не менее чем 5% из этих рабочих мест, для которых используется поддержка нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="190a9-125">Microsoft 365 Multi-Geo is available as an add-on to the following Microsoft 365 subscription plans for EA customers with a minimum of 250 Microsoft 365 seats in their tenant, and a minimum of 5% of those seats using multi-geo.</span></span> <span data-ttu-id="190a9-126">За дополнительной информацией обращайтесь к команде, в которую входит ваша учетная запись.</span><span class="sxs-lookup"><span data-stu-id="190a9-126">Please contact your Microsoft account team for details.</span></span>

- <span data-ttu-id="190a9-127">Microsoft 365 F1, E1, E3 или E5</span><span class="sxs-lookup"><span data-stu-id="190a9-127">Microsoft 365 F1, E1, E3, or E5</span></span>
- <span data-ttu-id="190a9-128">Exchange Online (план 1 или план 2)</span><span class="sxs-lookup"><span data-stu-id="190a9-128">Exchange Online Plan 1 or Plan 2</span></span>
- <span data-ttu-id="190a9-129">OneDrive для бизнеса (план 1 или план 2)</span><span class="sxs-lookup"><span data-stu-id="190a9-129">OneDrive for Business Plan 1 or Plan 2</span></span>
- <span data-ttu-id="190a9-130">SharePoint Online (план 1 или план 2)</span><span class="sxs-lookup"><span data-stu-id="190a9-130">SharePoint Online Plan 1 or Plan 2</span></span>

## <a name="microsoft-365-multi-geo-availability"></a><span data-ttu-id="190a9-131">Доступность Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="190a9-131">Microsoft 365 Multi-Geo availability</span></span>

<span data-ttu-id="190a9-132">В настоящее время Microsoft 365 Multi-Geo доступен в таких странах и регионах:</span><span class="sxs-lookup"><span data-stu-id="190a9-132">Microsoft 365 Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="190a9-133">Начало работы</span><span class="sxs-lookup"><span data-stu-id="190a9-133">Getting started</span></span>

<span data-ttu-id="190a9-134">Чтобы приступить к работе с несколькими регионами, следуйте указанным ниже инструкциям.</span><span class="sxs-lookup"><span data-stu-id="190a9-134">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="190a9-135">Совместно с группой специалистов, занимающихся учетными записями, добавьте план обслуживания _с поддержкой нескольких регионов в Microsoft 365_.</span><span class="sxs-lookup"><span data-stu-id="190a9-135">Work with your account team to add the _Multi-Geo Capabilities in Microsoft 365_ service plan.</span></span> <span data-ttu-id="190a9-136">Они помогут вам добавить необходимое количество лицензий.</span><span class="sxs-lookup"><span data-stu-id="190a9-136">They will guide you to add the number of licenses needed.</span></span> <span data-ttu-id="190a9-137">Функция поддержки нескольких регионов доступна клиентам EA с не менее 250 подписками на Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="190a9-137">Multi-Geo feature is available to EA customers with a minimum of 250 Microsoft 365 subscriptions.</span></span>

   <span data-ttu-id="190a9-138">Прежде чем вы сможете начать работу в Microsoft 365 Multi-Geo, корпорации Майкрософт потребуется настроить ваш клиент Exchange Online для поддержки нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="190a9-138">Before you can start using Microsoft 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="190a9-139">Этот разовый процесс настройки запускается после заказа плана обслуживания с *поддержкой нескольких регионов в Microsoft 365* и появления лицензий в вашем клиенте.</span><span class="sxs-lookup"><span data-stu-id="190a9-139">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Microsoft 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="190a9-140">Вы получите уведомления в [Центре сообщений Microsoft 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) после присвоения лицензий с поддержкой нескольких регионов и затем сможете начать настройку и использование возможностей Microsoft 365 Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="190a9-140">You'll receive notifications in the [Microsoft 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Microsoft 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="190a9-141">См. статью [Планирование среды с поддержкой нескольких регионов](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="190a9-141">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="190a9-142">Узнайте об [администрировании среды с поддержкой нескольких регионов](administering-a-multi-geo-environment.md) и о том, [как пользователи взаимодействуют со средой](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="190a9-142">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="190a9-143">Когда вы будете готовы настроить Microsoft 365 Multi-Geo, [настройте свой клиент для поддержки нескольких регионов](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="190a9-143">When you are ready to set up Microsoft 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="190a9-144">[Настройка поиска](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="190a9-144">[Set up search](configure-search-for-multi-geo.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="190a9-145">См. также</span><span class="sxs-lookup"><span data-stu-id="190a9-145">See also</span></span>

[<span data-ttu-id="190a9-146">Поддержка нескольких регионов в Exchange Online и OneDrive</span><span class="sxs-lookup"><span data-stu-id="190a9-146">Multi-Geo in Exchange Online and OneDrive</span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="190a9-147">Поддержка нескольких регионов в OneDrive и SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="190a9-147">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[<span data-ttu-id="190a9-148">Поддержка нескольких регионов в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="190a9-148">Multi-Geo Capabilities in Exchange Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)

[<span data-ttu-id="190a9-149">Взаимодействие групп в нескольких географических средах</span><span class="sxs-lookup"><span data-stu-id="190a9-149">Teams experience in a multi-geo environment</span></span>](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)
