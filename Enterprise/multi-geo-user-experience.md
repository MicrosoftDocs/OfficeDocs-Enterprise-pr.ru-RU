---
title: Взаимодействие с пользователем в среде multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Описание взаимодействия с пользователями SharePoint и OneDrive в среде с несколькими географически.
ms.openlocfilehash: 42e384d3e93ca3f5a06a8ee07a37b10e21477038
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="e0b9c-103">Взаимодействие с пользователем в среде с несколькими географически</span><span class="sxs-lookup"><span data-stu-id="e0b9c-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="e0b9c-104">Ниже приведен пользователи будут видеть в конфигурации с несколькими OneDrive-географически.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="e0b9c-105">Пользователя OneDrive для бизнеса расположения</span><span class="sxs-lookup"><span data-stu-id="e0b9c-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="e0b9c-p101">Пользователи будут иметь свои OneDrive для бизнеса, подготовить к работе в их расположения предпочитаемый данных. Если пользователь переходит на OneDrive URL-адрес, который содержит неправильные географического расположения (например, закладки из предыдущей географического расположения), они автоматически перенаправляются на страницу OneDrive в соответствующие географического расположения.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="e0b9c-108">Общий доступ</span><span class="sxs-lookup"><span data-stu-id="e0b9c-108">Sharing</span></span>

<span data-ttu-id="e0b9c-p102">"Выбор людей" опыт показывает всех пользователей, независимо от их географического расположения. Это позволяет пользователям совместно использовать с другим пользователем в их же географически или в любых других вашего клиента географического расположения. Содержимое из разных географического расположения будет отображаться в виде **со мной поделились** в пользователя OneDrive для бизнеса и может осуществляться с помощью интерфейса единого входа, независимо от того, какие географического расположения размещается в.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="e0b9c-112">Приложения Office</span><span class="sxs-lookup"><span data-stu-id="e0b9c-112">Office applications</span></span>

<span data-ttu-id="e0b9c-p103">При входе в приложениях Office, например Word, Excel и PowerPoint автоматически обнаруживает правильные OneDrive для географического расположения Business для каждого пользователя. Введите URL-адрес, относящиеся к географически для их OneDrive пользователям не нужно.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="e0b9c-115">OneDrive для бизнеса клиента синхронизации</span><span class="sxs-lookup"><span data-stu-id="e0b9c-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="e0b9c-116">OneDrive для бизнеса клиента синхронизации (версия 17.3.6943.0625 и более поздних версий) автоматически обнаруживает правильные OneDrive для бизнеса географически расположения для пользователя.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="e0b9c-117">Средство запуска приложений Office 365</span><span class="sxs-lookup"><span data-stu-id="e0b9c-117">Office 365 app launcher</span></span>

<span data-ttu-id="e0b9c-p104">Запуск приложения — ферма с несколькими-географически принять во внимание и переадресует каждой из них в соответствующие географически расположение рабочей нагрузки. OneDrive заголовков указывает на правильные географически расположение, где размещено библиотеки OneDrive пользователя, пока плитку SharePoint будет указывать всех пользователей центрального расположения, как веб-сайтов групп размещаются по-прежнему существует.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="e0b9c-120">Углубимся профили пользователей</span><span class="sxs-lookup"><span data-stu-id="e0b9c-120">Delve User profiles</span></span>

<span data-ttu-id="e0b9c-p105">Сведения о профилях пользователей создаются в географически расположение пользователя. При выборе пользователем, будет открыт в соответствующие географически расположение для пользователя, где вы увидите сведения о них полного профиля.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="e0b9c-123">Если Delve отключена, будет доступно классический профиль опытом SharePoint, который не multi географически принять во внимание.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="e0b9c-124">Delve</span><span class="sxs-lookup"><span data-stu-id="e0b9c-124">Delve</span></span>

<span data-ttu-id="e0b9c-125">Для пользователей Office 365, в экземпляры вспомогательных поддерживается углубимся несколькими географически, с ограничением, Delve не ссылка на записи блога SharePoint, созданным пользователями в других регионах, только на свои сайты SharePoint блога.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="e0b9c-126">Поиск</span><span class="sxs-lookup"><span data-stu-id="e0b9c-126">Search</span></span>

<span data-ttu-id="e0b9c-p106">Каждое местоположение географически имеет свой собственный центр поиска и индекс поиска. При выполнении пользователем поиска, запрос отправляется в расположениях географически и объединенных и затем ранжирования, пользователь получает объединенные результаты возвращаемых результатов. Пользователи получают результаты из всех расположений географически вне зависимости от географического расположения. В разделе [Настройка поиска для OneDrive для бизнеса Multi-географически](configure-search-for-multi-geo.md) особенности.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="e0b9c-131">Поддерживаются следующие клиенты поиска:</span><span class="sxs-lookup"><span data-stu-id="e0b9c-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="e0b9c-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="e0b9c-132">OneDrive for Business</span></span>

-   <span data-ttu-id="e0b9c-133">Delve</span><span class="sxs-lookup"><span data-stu-id="e0b9c-133">Delve</span></span>

-   <span data-ttu-id="e0b9c-134">Домашняя страница SharePoint</span><span class="sxs-lookup"><span data-stu-id="e0b9c-134">SharePoint Home</span></span>

-   <span data-ttu-id="e0b9c-135">Центр поиска</span><span class="sxs-lookup"><span data-stu-id="e0b9c-135">The Search Center</span></span>

-   <span data-ttu-id="e0b9c-136">Настраиваемые приложения поиска, использующие API поиска SharePoint</span><span class="sxs-lookup"><span data-stu-id="e0b9c-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="e0b9c-137">Операций ввода-вывода OneDrive и Android (en)</span><span class="sxs-lookup"><span data-stu-id="e0b9c-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="e0b9c-p107">Операций ввода-вывода OneDrive и Android мобильных приложениях покажу файлы OneDrive и предоставлен вне зависимости от их географического расположения файлов. Поиск в мобильных приложениях OneDrive будут отображаться релевантные результаты из всех расположений географически. Загрузите последние версии этих приложений.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="e0b9c-141">Использование [OneDrive на операций ввода-вывода](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) и [Использования OneDrive для Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) более подробные сведения.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="e0b9c-142">Взаимодействие группы</span><span class="sxs-lookup"><span data-stu-id="e0b9c-142">Teams Experience</span></span>

<span data-ttu-id="e0b9c-p108">Группы — ферма с несколькими географически принять во внимание. Файлы OneDrive и недавно просматриваемые отображаются независимо от географического расположения пользователя. @ упоминания могли работать с пользователями из всех географического расположения.</span><span class="sxs-lookup"><span data-stu-id="e0b9c-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
