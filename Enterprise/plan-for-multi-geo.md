---
title: Планирование использования OneDrive для бизнеса с поддержкой нескольких регионов
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
description: Сведения о OneDrive для бизнеса с поддержкой нескольких регионов, о принципе такой поддержки и о географических расположениях, доступных для хранения данных.
ms.openlocfilehash: d40f84ea3636b4eca2711a48bd9d70c73a242cfd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849865"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="8b366-103">Планирование использования OneDrive для бизнеса с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="8b366-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="8b366-104">Настоящее руководство предназначено для администраторов транснациональных компаний (MNC), которые готовятся использовать клиент SharePoint Online в дополнительных географических расположениях и при этом должны соблюдать требования к местонахождению данных.</span><span class="sxs-lookup"><span data-stu-id="8b366-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="8b366-p101">В конфигурации OneDrive с поддержкой нескольких регионов клиент Office 365 предусматривает наличие центрального расположения и одного или нескольких периферийных географических расположений. Это один клиент, который охватывает несколько географических расположений. В случае OneDrive с поддержкой нескольких регионов управление данными клиента, в том числе теми, которые касаются географических расположений, выполняется в Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="8b366-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="8b366-108">Ниже приведены некоторые ключевые термины, связанные с поддержкой нескольких регионов, которые помогут вам понять базовые концепции конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8b366-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="8b366-109">**Клиент** — представление организации в облаке Office 365, которое имеет, как правило, один или несколько связанных с ним доменов (например, http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="8b366-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="8b366-110">**Географические расположения** — географические расположения, доступные для размещения данных в клиенте Office 365.</span><span class="sxs-lookup"><span data-stu-id="8b366-110">**Geo locations** – The geographic locations available to host data in an Office 365 tenant.</span></span>

-   <span data-ttu-id="8b366-p102">**Периферийные расположения** — географические расположения, которые вы настроили для размещения данных в своем клиенте Office 365. Клиенты с поддержкой нескольких регионов охватывают более одного географического расположения (например, Северную Америку и Европу).</span><span class="sxs-lookup"><span data-stu-id="8b366-p102">**Satellite locations** – The geo locations that you have configured to host data in your Office 365 tenant. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="8b366-p103">**Предпочтительное расположение данных (PDL)**  — географическое расположение, в котором хранятся данные OneDrive отдельного пользователя. В качестве PDL администратор может указать любое из настроенных для клиента разрешенных расположений данных. Обратите внимание на то, что в случае изменения PDL для пользователя, у которого уже есть сайт OneDrive, данные OneDrive не переместятся в новое географическое расположение автоматически. Дополнительные сведения см. в статье [Перемещение библиотеки OneDrive в другое географическое расположение](move-onedrive-between-geo-locations.md).</span><span class="sxs-lookup"><span data-stu-id="8b366-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="8b366-117">Чтобы включить поддержку нескольких регионов, выполните четыре основных шага:</span><span class="sxs-lookup"><span data-stu-id="8b366-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="8b366-118">Совместно с группой специалистов, занимающихся учетными записями, добавьте план обслуживания _с поддержкой нескольких регионов в Office 365_.</span><span class="sxs-lookup"><span data-stu-id="8b366-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="8b366-119">Выберите необходимые периферийные расположения и добавьте их для клиента.</span><span class="sxs-lookup"><span data-stu-id="8b366-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="8b366-p104">Задайте требуемое периферийное расположение, которое выбрали, как PDL пользователя. Новый сайт OneDrive для пользователя будет подготовлен к работе с учетом PDL.</span><span class="sxs-lookup"><span data-stu-id="8b366-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="8b366-122">При необходимости перенесите существующие сайты OneDrive пользователя из центрального расположения в предпочтительное расположение данных.</span><span class="sxs-lookup"><span data-stu-id="8b366-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="8b366-123">Все упомянутые шаги подробно описаны в статье [Настройка OneDrive для бизнеса с поддержкой нескольких регионов](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8b366-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b366-p105">Обратите внимание на то, что поддержка нескольких регионов в Office 365 предназначена не для оптимизации производительности, а для выполнения требований к местонахождению данных. Для получения сведений об оптимизации производительности в Office 365 см. статью [Планирование сети и настройка производительности для Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) или обратитесь в группу поддержки.</span><span class="sxs-lookup"><span data-stu-id="8b366-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="8b366-p106">Вы можете настроить любое из приведенных ниже расположений как периферийное расположение для размещения файлов OneDrive. Планируя поддержку нескольких регионов, составьте список расположений, которые хотите добавить для клиента Office 365. Рекомендуем начать с одного или двух периферийных расположений и постепенно добавлять новые по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="8b366-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="8b366-129"><strong>Расположение</strong></span><span class="sxs-lookup"><span data-stu-id="8b366-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="8b366-130"><strong>Код</strong></span><span class="sxs-lookup"><span data-stu-id="8b366-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="8b366-131">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="8b366-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="8b366-132">APC</span><span class="sxs-lookup"><span data-stu-id="8b366-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8b366-133">Австралия</span><span class="sxs-lookup"><span data-stu-id="8b366-133">Australia</span></span></td>
<td align="left"><span data-ttu-id="8b366-134">AUS</span><span class="sxs-lookup"><span data-stu-id="8b366-134">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b366-135">Канада</span><span class="sxs-lookup"><span data-stu-id="8b366-135">Canada</span></span></td>
<td align="left"><span data-ttu-id="8b366-136">CAN</span><span class="sxs-lookup"><span data-stu-id="8b366-136">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8b366-137">Европа, Ближний Восток и Африка</span><span class="sxs-lookup"><span data-stu-id="8b366-137">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="8b366-138">EUR</span><span class="sxs-lookup"><span data-stu-id="8b366-138">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b366-139">Франция</span><span class="sxs-lookup"><span data-stu-id="8b366-139">France</span></span></td>
<td align="left"><span data-ttu-id="8b366-140">FRA</span><span class="sxs-lookup"><span data-stu-id="8b366-140">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b366-141">Япония</span><span class="sxs-lookup"><span data-stu-id="8b366-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="8b366-142">JPN</span><span class="sxs-lookup"><span data-stu-id="8b366-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8b366-143">Республика Корея</span><span class="sxs-lookup"><span data-stu-id="8b366-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="8b366-144">KOR</span><span class="sxs-lookup"><span data-stu-id="8b366-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b366-145">Северная Америка</span><span class="sxs-lookup"><span data-stu-id="8b366-145">North America</span></span></td>
<td align="left"><span data-ttu-id="8b366-146">NAM</span><span class="sxs-lookup"><span data-stu-id="8b366-146">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b366-147">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="8b366-147">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="8b366-148">GBR</span><span class="sxs-lookup"><span data-stu-id="8b366-148">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="8b366-149">Ожидается поддержка таких географических расположений:</span><span class="sxs-lookup"><span data-stu-id="8b366-149">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="8b366-150">Индия</span><span class="sxs-lookup"><span data-stu-id="8b366-150">India</span></span>

<span data-ttu-id="8b366-p107">Настраивая поддержку нескольких регионов, рассмотрите возможность консолидировать свою локальную инфраструктуру при миграции в Office 365. Например, можно консолидировать локальные фермы, находящиеся в Сингапуре и Малайзии, с периферийным расположением APC при условии, что это разрешено требованиями к местонахождению данных.</span><span class="sxs-lookup"><span data-stu-id="8b366-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="8b366-153">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="8b366-153">Best practices</span></span>

<span data-ttu-id="8b366-p108">Рекомендуем создать тестового пользователя в Office 365 для выполнения первоначального тестирования. Далее приведены некоторые шаги, касающиеся тестирования и проверки с вовлечением этого пользователя. Выполнив их, вы сможете начать подключение пользователей рабочей среды к OneDrive с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="8b366-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="8b366-p109">Завершив тестирование с вовлечением тестового пользователя, выберите пилотную группу (например, группу ИТ-специалистов), которая первой воспользуется OneDrive в новом географическом расположении. В эту группу добавьте пользователей, у которых еще нет OneDrive. Рекомендуем вначале добавлять не более пяти человек, а затем постепенно расширять группу методом пакетного развертывания.</span><span class="sxs-lookup"><span data-stu-id="8b366-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="8b366-p110">У каждого пользователя должно быть *предпочтительное расположение данных* (PDL), чтобы служба Office 365 могла определить, в каком географическом расположении нужно подготовить к работе OneDrive. PDL пользователя должно соответствовать одному из выбранных периферийных расположений или центральному расположению. Хотя поле PDL можно не заполнять, рекомендуем задать его для всех пользователей. Рабочие нагрузки пользователя без PDL будут подготовлены к работе в центральном расположении.</span><span class="sxs-lookup"><span data-stu-id="8b366-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="8b366-p111">Создайте список пользователей, включите имя участника-пользователя и код расположения для соответствующего предпочтительного расположения данных. Включите тестового пользователя и первоначальную пилотную группу. Этот список понадобится для процедур настройки.</span><span class="sxs-lookup"><span data-stu-id="8b366-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="8b366-p112">Если выполняется синхронизация пользователей из локальной системы Active Directory в Azure Active Directory, нужно установить предпочтительное расположение данных для синхронизируемых пользователей с помощью Azure Active Directory Connect. Напрямую настроить PDL для синхронизируемых пользователей с помощью Azure AD PowerShell невозможно. Шаги по настройке PDL в AD и синхронизации приведены в статье [Синхронизация Azure Active Directory Connect: настройка предпочтительного расположения данных для ресурсов Office 365](https://docs.microsoft.com/ru-RU/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="8b366-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/ru-RU/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="8b366-p113">Администрирование клиента с поддержкой нескольких регионов может отличаться от администрирования без таковой, так как многие службы и настройки SharePoint и OneDrive поддерживают несколько регионов. Рекомендуем ознакомиться со статьей [Администрирование среды с поддержкой нескольких регионов](administering-a-multi-geo-environment.md), прежде чем переходить к настройке.</span><span class="sxs-lookup"><span data-stu-id="8b366-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="8b366-171">Прочтите статью [Взаимодействие с пользователем в среде с поддержкой нескольких регионов](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="8b366-171">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="8b366-172">Прежде чем начать настройку OneDrive для бизнеса с поддержкой нескольких регионов, прочтите статью [Настройка OneDrive для бизнеса с поддержкой нескольких регионов](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8b366-172">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="8b366-173">После настройки не забудьте [перенести библиотеки OneDrive пользователей](move-onedrive-between-geo-locations.md), если это необходимо для работы пользователей в предпочтительных расположениях данных.</span><span class="sxs-lookup"><span data-stu-id="8b366-173">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
