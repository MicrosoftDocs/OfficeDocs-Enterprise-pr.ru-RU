---
title: Взаимодействие с пользователем в среде с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Сведения о взаимодействии с пользователем SharePoint и OneDrive в среде с поддержкой нескольких регионов.
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="68bda-103">Взаимодействие с пользователем в среде с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="68bda-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="68bda-104">Ниже показано то, что увидят пользователи в конфигурации OneDrive с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="68bda-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="68bda-105">Расположение OneDrive для бизнеса пользователя</span><span class="sxs-lookup"><span data-stu-id="68bda-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="68bda-p101">Служба OneDrive для бизнеса будет подготовлена к работе в предпочтительном расположении данных пользователя. Если он перейдет по URL-адресу OneDrive, содержащему неправильные сведения о геообъекте (например, по закладке для предыдущего геообъекта), то будет автоматически перенаправлен на OneDrive в правильном географическом расположении.</span><span class="sxs-lookup"><span data-stu-id="68bda-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="68bda-108">Доступ</span><span class="sxs-lookup"><span data-stu-id="68bda-108">Sharing</span></span>

<span data-ttu-id="68bda-p102">В средстве выборе людей отображаются все пользователи независимо от их географического расположения. Поэтому один пользователь может делиться с другим, находящимся в том же или любом другом географическом расположении клиента. Содержимое из разных географических расположений будет отображаться в представлении **Мне предоставлен доступ** в пользовательском OneDrive для бизнеса. Это содержимое будет доступно с помощью единого входа независимо от того, в каком географическом расположении размещено.</span><span class="sxs-lookup"><span data-stu-id="68bda-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="68bda-112">Приложения Office</span><span class="sxs-lookup"><span data-stu-id="68bda-112">Office applications</span></span>

<span data-ttu-id="68bda-p103">Такие приложения Office, как Word, Excel и PowerPoint, будут автоматически обнаруживать правильное географическое расположение OneDrive для бизнеса для каждого пользователя, когда тот будет выполнять вход. Пользователям не нужно вводить специальный URL-адрес для OneDrive с учетом региона.</span><span class="sxs-lookup"><span data-stu-id="68bda-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="68bda-115">Клиент синхронизации OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="68bda-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="68bda-116">Клиент синхронизации OneDrive для бизнеса (версии 17.3.6943.0625 или новее) будет автоматически обнаруживать правильное географическое расположение OneDrive для бизнеса для пользователя.</span><span class="sxs-lookup"><span data-stu-id="68bda-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="68bda-117">Средство запуска приложений Office 365</span><span class="sxs-lookup"><span data-stu-id="68bda-117">Office 365 app launcher</span></span>

<span data-ttu-id="68bda-p104">Средство запуска приложений поддерживает несколько регионов и будет выполнять перенаправление для каждой плитки в соответствующее географическое расположение рабочей нагрузки. Плитка OneDrive указывает на правильное географическое расположение, в котором размещена пользовательская библиотека OneDrive, в то время как плитка SharePoint будет направлять всех пользователей в центральное расположение, так как сайты групп по-прежнему размещены там.</span><span class="sxs-lookup"><span data-stu-id="68bda-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="68bda-120">Профили пользователей Delve</span><span class="sxs-lookup"><span data-stu-id="68bda-120">Delve User profiles</span></span>

<span data-ttu-id="68bda-p105">Управление данными профиля пользователя выполняется в географическом расположении пользователя. При выборе пользователя вы будете перенаправлены в его соответствующее географическое расположение, где увидите полные сведения профиля.</span><span class="sxs-lookup"><span data-stu-id="68bda-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="68bda-123">Если служба Delve выключена, отобразится классический интерфейс профиля в SharePoint без поддержки нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="68bda-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="68bda-124">Delve</span><span class="sxs-lookup"><span data-stu-id="68bda-124">Delve</span></span>

<span data-ttu-id="68bda-125">Для пользователей Office 365 в периферийных экземплярах доступна служба Delve с поддержкой нескольких регионов. Но при этом существует ограничение: Delve не ссылается на записи блога SharePoint, созданные пользователями в других регионах.</span><span class="sxs-lookup"><span data-stu-id="68bda-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="68bda-126">Поиск</span><span class="sxs-lookup"><span data-stu-id="68bda-126">Search</span></span>

<span data-ttu-id="68bda-p106">Для каждого географического расположения предусмотрены отдельные индекс поиска и центр поиска. Когда пользователь выполняет поиск, запрос отправляется во все географические расположения, а возвращенные результаты объединяются и затем ранжируются. Пользователи получают результаты из всех географических расположений независимо от того, где находятся. Более подробные сведения см. в статье [Настройка поиска для OneDrive для бизнеса с поддержкой нескольких регионов](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="68bda-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="68bda-131">Поддерживаемые клиенты поиска:</span><span class="sxs-lookup"><span data-stu-id="68bda-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="68bda-132">OneDrive для бизнеса;</span><span class="sxs-lookup"><span data-stu-id="68bda-132">OneDrive for Business</span></span>

-   <span data-ttu-id="68bda-133">Delve;</span><span class="sxs-lookup"><span data-stu-id="68bda-133">Delve</span></span>

-   <span data-ttu-id="68bda-134">домашняя страница SharePoint;</span><span class="sxs-lookup"><span data-stu-id="68bda-134">SharePoint Home</span></span>

-   <span data-ttu-id="68bda-135">центр поиска;</span><span class="sxs-lookup"><span data-stu-id="68bda-135">The Search Center</span></span>

-   <span data-ttu-id="68bda-136">специальные поисковые приложения, использующие API поиска SharePoint.</span><span class="sxs-lookup"><span data-stu-id="68bda-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="68bda-137">OneDrive для iOS и Android</span><span class="sxs-lookup"><span data-stu-id="68bda-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="68bda-p107">Мобильные приложения OneDrive для iOS и Android будут отображать ваши файлы OneDrive и файлы, к которым вам предоставлен доступ, независимо от их географического расположения. Выполнив поиск из мобильных приложений OneDrive, вы увидите релевантные результаты из всех географических расположений. Скачайте последние версии этих приложений.</span><span class="sxs-lookup"><span data-stu-id="68bda-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="68bda-141">Дополнительные сведения см. в статьях [Работа с OneDrive в iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) и [Использование OneDrive на устройстве с Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36).</span><span class="sxs-lookup"><span data-stu-id="68bda-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="68bda-142">Работа в Teams</span><span class="sxs-lookup"><span data-stu-id="68bda-142">Teams Experience</span></span>

<span data-ttu-id="68bda-p108">Teams поддерживает несколько регионов. Файлы OneDrive, а также недавно просмотренные файлы отображаются независимо от географического расположения пользователя. @упоминания доступны для пользователей из всех географических расположений.</span><span class="sxs-lookup"><span data-stu-id="68bda-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
