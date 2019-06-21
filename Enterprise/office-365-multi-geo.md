---
title: Office 365 с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Расширьте свою географию присутствия Office 365 с помощью поддержки нескольких регионов в Office 365.
ms.openlocfilehash: 7aa1933725617bcc1f84bbe6d0f31a6ddd91815d
ms.sourcegitcommit: a7b2adf4b55df5fc35a617a145e8177caefce28b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2019
ms.locfileid: "35078513"
---
# <a name="office-365-multi-geo"></a><span data-ttu-id="74ef0-103">Office 365 с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="74ef0-103">Office 365 Multi-Geo</span></span>

<span data-ttu-id="74ef0-104">Поддержка нескольких регионов в Office 365 позволяет организации развивать бизнес в нескольких географических регионах или странах, используя существующий клиент Office 365.</span><span class="sxs-lookup"><span data-stu-id="74ef0-104">With Office 365 Multi-Geo, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="74ef0-105">Обратитесь в отдел по работе с клиентами Майкрософт, чтобы зарегистрировать свою международную компанию для работы с несколькими регионами в Office 365.</span><span class="sxs-lookup"><span data-stu-id="74ef0-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Office 365 Multi-Geo.</span></span>
  
<span data-ttu-id="74ef0-106">Поддержка нескольких регионов в Office 365 позволяет подготавливать и хранить неактивные данные в выбранных вами регионах, а также предоставлять современные возможности для работы всем сотрудникам.</span><span class="sxs-lookup"><span data-stu-id="74ef0-106">With Office 365 Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="74ef0-107">Видео: знакомство с Office 365 с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="74ef0-107">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="74ef0-108">В среде с поддержкой нескольких регионов клиент Office 365 состоит из центрального расположения (где изначально подготавливается подписка на Office 365) и одного или нескольких периферийных расположений.</span><span class="sxs-lookup"><span data-stu-id="74ef0-108">In a Multi-Geo environment, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="74ef0-109">В клиенте с несколькими регионами информация о регионах, группах и пользователях обрабатывается в Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="74ef0-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="74ef0-110">Так как информация клиента обрабатывается централизованно и синхронизируется с каждым регионом, общий доступ и возможности в компании носят глобальный характер.</span><span class="sxs-lookup"><span data-stu-id="74ef0-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![Снимок экрана: карта нескольких регионов в Центре администрирования SharePoint](media/multi-geo-world-map.png)

<span data-ttu-id="74ef0-112">Обратите внимание, что функция поддержки нескольких регионов в Office 365 изначально не предназначена для повышения производительности. Она предназначена для соблюдения требований по расположению данных.</span><span class="sxs-lookup"><span data-stu-id="74ef0-112">Note that Office 365 Multi-Geo is not primarily designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="74ef0-113">Сведения о повышении производительности для Office 365 см. в статье [Планирование сети и настройка производительности для Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) или обратитесь к группе поддержки.</span><span class="sxs-lookup"><span data-stu-id="74ef0-113">For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="74ef0-114">Терминология</span><span class="sxs-lookup"><span data-stu-id="74ef0-114">Terminology</span></span>

<span data-ttu-id="74ef0-115">Ниже указаны основные термины, используемые при описании Office 365 с поддержкой нескольких регионов:</span><span class="sxs-lookup"><span data-stu-id="74ef0-115">Here are the key terms used in describing Office 365 Multi-Geo:</span></span>

- <span data-ttu-id="74ef0-116">**Центральное расположение** — географическое расположение, в котором изначально подготовлен клиент.</span><span class="sxs-lookup"><span data-stu-id="74ef0-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="74ef0-117">**Администратор геообъекта** — администратор, который может управлять одним или несколькими периферийными расположениями.</span><span class="sxs-lookup"><span data-stu-id="74ef0-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="74ef0-118">**Код региона** — код из трех букв для определенного географического расположения.</span><span class="sxs-lookup"><span data-stu-id="74ef0-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="74ef0-119">**Географическое расположение** — регион, который можно использовать в клиенте с поддержкой нескольких регионов для размещения данных, включая почтовые ящики Exchange, а также сайты OneDrive и SharePoint.</span><span class="sxs-lookup"><span data-stu-id="74ef0-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="74ef0-120">**Предпочтительное расположение данных (PDL)** — свойство пользователя, устанавливаемое администратором, которое указывает географическое расположение, где следует подготовить почтовый ящик Exchange и хранилище OneDrive пользователей.</span><span class="sxs-lookup"><span data-stu-id="74ef0-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="74ef0-121">PDL также определяет, где подготовлены сайты SharePoint, созданные пользователем.</span><span class="sxs-lookup"><span data-stu-id="74ef0-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="74ef0-122">**Периферийное расположение** — географическое расположение, где учитывающие регион рабочие нагрузки Office 365 (SharePoint, OneDrive и Exchange) включены в клиенте с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="74ef0-122">**Satellite location** – The geo locations where the geo-aware Office 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="74ef0-123">**Клиент** — представление организации в Office 365, которое имеет, как правило, один или несколько связанных с ним доменов (например, contoso.com).</span><span class="sxs-lookup"><span data-stu-id="74ef0-123">**Tenant** – An organization's representation in Office 365 which typically has one or more domains associated with it (for example, contoso.com).</span></span>

## <a name="office-365-multi-geo-availability"></a><span data-ttu-id="74ef0-124">Доступность поддержки нескольких регионов в Office 365</span><span class="sxs-lookup"><span data-stu-id="74ef0-124">Office 365 Multi-Geo availability</span></span>

<span data-ttu-id="74ef0-125">В настоящее время поддержка нескольких регионов в Office 365 доступна в таких странах и регионах:</span><span class="sxs-lookup"><span data-stu-id="74ef0-125">Office 365 Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="74ef0-126">Начало работы</span><span class="sxs-lookup"><span data-stu-id="74ef0-126">Getting started</span></span>

<span data-ttu-id="74ef0-127">Чтобы приступить к работе с несколькими регионами, следуйте указанным ниже инструкциям.</span><span class="sxs-lookup"><span data-stu-id="74ef0-127">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="74ef0-128">Совместно с группой специалистов, занимающихся учетными записями, добавьте план обслуживания _с поддержкой нескольких регионов в Office 365_.</span><span class="sxs-lookup"><span data-stu-id="74ef0-128">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span> <span data-ttu-id="74ef0-129">Они помогут вам добавить необходимое количество лицензий.</span><span class="sxs-lookup"><span data-stu-id="74ef0-129">They will guide you to add the number of licenses needed.</span></span> <span data-ttu-id="74ef0-130">Функция поддержки нескольких регионов доступна клиентам с не менее 500 подписками на Office 365.</span><span class="sxs-lookup"><span data-stu-id="74ef0-130">Multi-Geo feature is available to customers with a minimum of 2,500 Office 365 subscriptions.</span></span>

   <span data-ttu-id="74ef0-131">Прежде чем вы сможете начать работу в Office 365 с поддержкой нескольких регионов корпорации Майкрософт потребуется настроить ваш клиент Exchange Online для поддержки нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="74ef0-131">Before you can start using Office 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="74ef0-132">Этот разовый процесс настройки запускается после заказа плана обслуживания с *функциями поддержки нескольких регионов в Office 365* и появления лицензий в вашем клиенте.</span><span class="sxs-lookup"><span data-stu-id="74ef0-132">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Office 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="74ef0-133">Вы получите уведомления в [Центре сообщений Office 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) после присвоения лицензий с поддержкой нескольких регионов и затем сможете начать настройку и использование функций поддержки нескольких регионов в Office 365.</span><span class="sxs-lookup"><span data-stu-id="74ef0-133">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Office 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="74ef0-134">См. статью [Планирование среды с поддержкой нескольких регионов](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="74ef0-134">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="74ef0-135">Узнайте об [администрировании среды с поддержкой нескольких регионов](administering-a-multi-geo-environment.md) и о том, [как пользователи взаимодействуют со средой](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="74ef0-135">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="74ef0-136">Когда вы будете готовы настроить Office 365 с поддержкой нескольких регионов, [настройте свой клиент для поддержки нескольких регионов](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="74ef0-136">When you are ready to set up Office 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="74ef0-137">[Настройка поиска](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="74ef0-137">[Set up search](configure-search-for-multi-geo.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74ef0-138">См. также</span><span class="sxs-lookup"><span data-stu-id="74ef0-138">See also</span></span>

[<span data-ttu-id="74ef0-139">Поддержка нескольких регионов в Exchange Online и OneDrive</span><span class="sxs-lookup"><span data-stu-id="74ef0-139">Multi-Geo in Exchange Online and OneDrive</span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="74ef0-140">Поддержка нескольких регионов в OneDrive и SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="74ef0-140">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[<span data-ttu-id="74ef0-141">Поддержка нескольких регионов в Exchange Online</span><span class="sxs-lookup"><span data-stu-id="74ef0-141">Multi-Geo Capabilities in Exchange Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)
