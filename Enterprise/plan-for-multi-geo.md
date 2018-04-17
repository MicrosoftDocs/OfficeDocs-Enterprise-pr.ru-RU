---
title: Планирование использования службы OneDrive для бизнеса Multi географически
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Сведения о OneDrive для различных бизнес-географически, как работает несколькими географически и какие географического расположения, доступны для хранения данных.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="ae765-103">Планирование использования службы OneDrive для бизнеса Multi географически</span><span class="sxs-lookup"><span data-stu-id="ae765-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="ae765-104">Данное руководство предназначено для администраторов глобальной экономике компаний (MNCs), подготавливающих их SharePoint Online клиента, чтобы развернуть, чтобы дополнительные географических зон в соответствии с присутствия компании в соответствии с требованиями объемом данных.</span><span class="sxs-lookup"><span data-stu-id="ae765-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="ae765-p101">В конфигурации с несколькими OneDrive-географически клиента Office 365 состоит из центрального расположения (также известной как расположение по умолчанию) и одно или несколько расположений географически вспомогательных. Это одним клиентом, которая распределена среди в нескольких подразделениях географически. Ферма с несколькими OneDrive-географически, данные клиента, включая географического расположения управляется в Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="ae765-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="ae765-108">Вот некоторые ключевые несколькими географически термины помогут вам понять основные понятия конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ae765-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="ae765-109">**Клиент** – представление организации в облако Office 365, который обычно имеет один или несколько доменов, связанных с ним (например, http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="ae765-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="ae765-p102">**Географического расположения** – географического расположения, где размещены данные вашего клиента. Географическая ферма с несколькими клиентами охватывать несколько местоположений географически, к примеру, Северной Америки и Европы.</span><span class="sxs-lookup"><span data-stu-id="ae765-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="ae765-112">**Допускается данных расположения (ADL)** — географически расположения, для которых настроен вашего клиента для размещения данных OneDrive и SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ae765-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="ae765-p103">**Предпочтительная расположение данных (PDL)** — географически расположение, где хранятся данные OneDrive отдельного пользователя. Это может иметь значение администратором, на какие-либо из расположений данных разрешены, настроенных для клиента. Обратите внимание, что при изменении PDL для пользователя, который уже связан сайт OneDrive их OneDrive данные не перемещаются в новое местоположение географически автоматически. Для получения дополнительных сведений в разделе [Перемещение библиотеки OneDrive для разных географического расположения](move-onedrive-between-geo-locations.md) .</span><span class="sxs-lookup"><span data-stu-id="ae765-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="ae765-117">Включение несколькими географически требует четырех основных шагов:</span><span class="sxs-lookup"><span data-stu-id="ae765-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="ae765-118">Работа с коллегами учетной записи для добавления план обслуживания _Несколькими географически возможности в Office 365_ .</span><span class="sxs-lookup"><span data-stu-id="ae765-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="ae765-119">Выберите на желаемую вспомогательные географически местоположений и добавить их к клиенту.</span><span class="sxs-lookup"><span data-stu-id="ae765-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="ae765-p104">Задайте расположение предпочитаемый данных пользователей к месту географически необходимые вспомогательные. При подготовке нового сайта OneDrive для пользователя, он может их PDL.</span><span class="sxs-lookup"><span data-stu-id="ae765-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="ae765-122">Перенос существующих сайтов OneDrive пользователей из дома в их расположение предпочитаемый данных при необходимости.</span><span class="sxs-lookup"><span data-stu-id="ae765-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="ae765-123">В разделе [Настройка OneDrive для бизнеса Multi-географически](multi-geo-tenant-configuration.md) для получения дополнительных сведений на каждый из этих шагов.</span><span class="sxs-lookup"><span data-stu-id="ae765-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae765-p105">Обратите внимание, что ферма с несколькими географически компонентов Office 365 не предназначены для оптимизации производительности случаях они предназначенные для удовлетворения требований к данным местонахождения. Сведения об оптимизации производительности для Office 365 [Планирование сети](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) и настройка производительности для Office 365 или обратитесь в группу поддержки.</span><span class="sxs-lookup"><span data-stu-id="ae765-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="ae765-p106">Можно настроить любые из следующих расположений быть расположения географически вспомогательных, где вы можете размещать файлы OneDrive. Во время планирования для различных географически, для создания списка расположений, которые вы хотите добавить в клиент Office 365. Мы рекомендуем начиная с одним или двумя вспомогательных расположения и затем постепенно расширятся, создавая дополнительные географического расположения, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="ae765-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ae765-129"><strong>Расположение</strong></span><span class="sxs-lookup"><span data-stu-id="ae765-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="ae765-130"><strong>Код</strong></span><span class="sxs-lookup"><span data-stu-id="ae765-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ae765-131">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="ae765-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="ae765-132">APC</span><span class="sxs-lookup"><span data-stu-id="ae765-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ae765-133">Европа / Средний Восток и Африка</span><span class="sxs-lookup"><span data-stu-id="ae765-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="ae765-134">ЕВРО</span><span class="sxs-lookup"><span data-stu-id="ae765-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ae765-135">Северная Америка</span><span class="sxs-lookup"><span data-stu-id="ae765-135">North America</span></span></td>
<td align="left"><span data-ttu-id="ae765-136">ИМ</span><span class="sxs-lookup"><span data-stu-id="ae765-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ae765-137">Австралия</span><span class="sxs-lookup"><span data-stu-id="ae765-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="ae765-138">СТАНДАРТНОЕ</span><span class="sxs-lookup"><span data-stu-id="ae765-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ae765-139">Канада</span><span class="sxs-lookup"><span data-stu-id="ae765-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="ae765-140">МОЖНО</span><span class="sxs-lookup"><span data-stu-id="ae765-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ae765-141">Япония</span><span class="sxs-lookup"><span data-stu-id="ae765-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="ae765-142">ЯПОНСКИЙ</span><span class="sxs-lookup"><span data-stu-id="ae765-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ae765-143">Корея</span><span class="sxs-lookup"><span data-stu-id="ae765-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="ae765-144">КОРЕЙСКИЙ</span><span class="sxs-lookup"><span data-stu-id="ae765-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ae765-145">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="ae765-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="ae765-146">GBR</span><span class="sxs-lookup"><span data-stu-id="ae765-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="ae765-147">Скоро:</span><span class="sxs-lookup"><span data-stu-id="ae765-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="ae765-148">Франция</span><span class="sxs-lookup"><span data-stu-id="ae765-148">France</span></span>
- <span data-ttu-id="ae765-149">Индия</span><span class="sxs-lookup"><span data-stu-id="ae765-149">India</span></span>

<span data-ttu-id="ae765-p107">При настройке несколькими географически проведите возможность консолидации локальной инфраструктуре во время миграции на Office 365. Например при наличии локальной фермы в Сингапур и Малайзия нажмите их можно объединить в расположение вспомогательных APC условии, что требования к местонахождения данных позволяют делать это.</span><span class="sxs-lookup"><span data-stu-id="ae765-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="ae765-152">Советы и рекомендации</span><span class="sxs-lookup"><span data-stu-id="ae765-152">Best practices</span></span>

<span data-ttu-id="ae765-p108">Рекомендуется создать тестового пользователя в Office 365 для начального тестирования. Мы рассмотрим некоторые этапы тестирования и проверки с этим пользователем прежде чем перейти к встроенным конечных пользователей в функцию OneDrive несколькими-географически.</span><span class="sxs-lookup"><span data-stu-id="ae765-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="ae765-p109">После выполнения тестирования с помощью тестового пользователя выберите пилотную – возможно из ИТ-отдел компании – к первым должен использовать OneDrive в новый географического расположения. Для первой группы выберите пользователей, которые еще не имеют OneDrive. Рекомендуется не более пяти пользователей в эту группу начальной и постепенно разверните трудозатрат пакетной выгрузка данных.</span><span class="sxs-lookup"><span data-stu-id="ae765-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="ae765-p110">Каждый пользователь должен иметь *расположение предпочитаемый данных* (PDL), чтобы Office 365 можно определить, в какой географически расположение для подготовки их OneDrive. Расположение пользователя предпочтительный данных должно соответствовать одному из к расположениям выбранного вспомогательных или центрального расположения. В поле PDL не является обязательным, рекомендуется задать PDL для всех пользователей. Рабочие нагрузки пользователя, не PDL будет выполнена подготовка в центрального расположения, на основе логики несколькими географически.</span><span class="sxs-lookup"><span data-stu-id="ae765-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="ae765-p111">Создание списка пользователей и включают в себя их имя участника-пользователя (UPN) и расположение кода для размещения соответствующих предпочитаемый данных. Со включают тестового пользователя и начальные пилотной группы. В этом списке потребуются процедуры настройки.</span><span class="sxs-lookup"><span data-stu-id="ae765-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="ae765-p112">Если пользователи синхронизируются из Active Directory (AD) в локальной системе для Azure Active Directory (AAD), необходимо задать расположение предпочитаемый данных для синхронизированных пользователей с помощью Azure Active Directory подключение. Расположение предпочитаемый данных для синхронизированных пользователей с помощью Windows Azure AD PowerShell нельзя настроить напрямую. Рассматривается процесс настройки PDL в AD и синхронизировать его в [Azure Active Directory подключение синхронизации: Настройка предпочитаемого данных расположения для ресурсов Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="ae765-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="ae765-p113">Администрирования клиента несколькими географически может отличаться от клиента несколькими географически, как многие из параметров SharePoint и OneDrive и службы, несколькими географически принять во внимание. Рекомендуется проверить [Администрирование среды ферма с несколькими географически](administering-a-multi-geo-environment.md) перед началом работы с конфигурацией.</span><span class="sxs-lookup"><span data-stu-id="ae765-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="ae765-170">Ознакомьтесь с [пользовательским интерфейсом в среде multgeo](multi-geo-user-experience.md) для получения дополнительных сведений о конечных пользователей в среде с несколькими географически.</span><span class="sxs-lookup"><span data-stu-id="ae765-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="ae765-171">Чтобы перед началом настройки OneDrive для бизнеса Multi-географически, обратитесь к разделу [Настройка OneDrive для бизнеса Multi-географически](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ae765-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="ae765-172">После выполнения настройки, не забудьте [перенос пользователей библиотеки OneDrive](move-onedrive-between-geo-locations.md) , чтобы получить от их расположения предпочитаемый данных пользователей.</span><span class="sxs-lookup"><span data-stu-id="ae765-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
