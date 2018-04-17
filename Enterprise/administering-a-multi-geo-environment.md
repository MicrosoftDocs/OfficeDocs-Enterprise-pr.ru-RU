---
title: Управление несколькими географически среды
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Сведения об администрировании служб SharePoint и OneDrive в среде с несколькими географически.
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="cc6b1-103">Управление несколькими географически среды</span><span class="sxs-lookup"><span data-stu-id="cc6b1-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="cc6b1-104">В этой статье приводятся в работе службы OneDrive и SharePoint в среде с несколькими географически.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="cc6b1-105">Интерфейс администратора OneDrive</span><span class="sxs-lookup"><span data-stu-id="cc6b1-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="cc6b1-p101">В [центре администрирования OneDrive](https://admin.onedrive.com) имеет **географического расположения** вкладки в левой области навигации сопоставить географического расположения компонентов, которые можно просматривать и управлять вашего географического расположения. Используйте эту страницу для добавления или удаления географического расположения для вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="cc6b1-108">Таксономии</span><span class="sxs-lookup"><span data-stu-id="cc6b1-108">Taxonomy</span></span>

<span data-ttu-id="cc6b1-p102">Мы поддерживаем объединенных [таксономии](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) для корпоративных управляемых метаданных в географически подразделениях с шаблоном, размещенной в центрального расположения для вашей компании. Рекомендуется управлять глобального таксономии из центрального расположения и только добавьте местоположениям их расположение вспомогательных географически таксономии. Глобальные таксономии термины будут синхронизированы с расположений географически вспомогательных.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="cc6b1-112">Общий доступ</span><span class="sxs-lookup"><span data-stu-id="cc6b1-112">Sharing</span></span>

<span data-ttu-id="cc6b1-p103">Администраторы могут задать и контроле политик общего доступа для каждого из их расположение. Сайты OneDrive в каждом расположении географически будет поддерживать только соответствующие географически конкретных параметры общего доступа. Например можно разрешить [внешний общий доступ](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) для центрального расположения, но не для вспомогательных расположение или наоборот. Для нескольких OneDrive-географически, необходимо управлять параметры общего доступа в каждом местоположении географически, как они не синхронизируется в клиента.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="cc6b1-p104">Для управления общего доступа посетить страницу [центра администрирования OneDrive параметры общего доступа](https://admin.onedrive.com/?v=SharingSettings) . По умолчанию с кем-либо в каждом расположение вспомогательных включена внешний общий доступ.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="cc6b1-119">Приложение профилей пользователей</span><span class="sxs-lookup"><span data-stu-id="cc6b1-119">User Profile Application</span></span>

<span data-ttu-id="cc6b1-p105">Существует [приложение профилей пользователей](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) в каждом расположении географически. Сведения о профиле каждого пользователя размещается в их географического расположения и доступны для администратора для данного географического расположения.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="cc6b1-122">Если у вас есть пользовательских свойств профилей, а затем мы рекомендуем использовать одну и ту же схему профилей на географических зон и заполнения вашей пользовательских свойств профилей в все географического расположения или при необходимости.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="cc6b1-123">Приложения BCS, Secure Store</span><span class="sxs-lookup"><span data-stu-id="cc6b1-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="cc6b1-124">BCS, службы Secure Store и приложения имеет отдельный географически экземпляры, таким образом администратору SharePoint Online необходимо управлять и настраивать эти службы из каждого экземпляра географически, которые требуется их присутствие.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="cc6b1-125">Безопасность и соответствие требованиям центра администрирования</span><span class="sxs-lookup"><span data-stu-id="cc6b1-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="cc6b1-126">Существует один центр центра соответствия для клиента несколькими географически: [Центр соответствия требованиям и безопасности Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="cc6b1-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="cc6b1-127">Сведения о защите (IP-адреса) данных потери Предотвращение (DLP) политики</span><span class="sxs-lookup"><span data-stu-id="cc6b1-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="cc6b1-p106">Можно задать защиты от потери данных на IP-адрес политик для OneDrive для бизнеса в центре безопасность и соответствие требованиям области политики при необходимости всей клиента или применимых пользователям. Например: Если вы хотите выберите политику для пользователя OneDrive в расположение вспомогательных, установите флажок, чтобы применить политику к определенным OneDrive и введите пользователя OneDrive URL-адрес. В разделе [Общие политик предотвращения потери данных](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) для Общие рекомендации по созданию политик защиты от потери данных.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="cc6b1-131">Политики защиты от потери данных автоматически синхронизируются зависимости от их применимость для каждого географического расположения.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="cc6b1-132">Реализация политики предотвращения потери данных и сведения о защите ко всем пользователям в любой папке на географически не параметр доступен в пользовательском Интерфейсе, вместо этого необходимо выбрать соответствующий учетных записей службы OneDrive для политики или применить политику глобально для всех учетных записей OneDrive.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="cc6b1-133">Обнаружение электронных данных</span><span class="sxs-lookup"><span data-stu-id="cc6b1-133">eDiscovery</span></span> 

<span data-ttu-id="cc6b1-p107">По умолчанию eDiscovery, руководитель или администратор клиента несколькими географически могут проводить eDiscovery только в центрального расположения, клиента. Для поддержки проводить eDiscovery для вспомогательных расположений, новый параметр Фильтр соответствия требованиям безопасности с именем «Область» доступна через PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="cc6b1-136">Глобальный администратор Office 365 необходимо назначить разрешения диспетчер обнаружения электронных данных, чтобы разрешить другим пользователям обнаружения электронных данных и назначение параметра «Области» в их применимых Фильтр соответствия требованиям безопасности для указания региона для проведения электронных данных как вспомогательные расположение, в противном случае — не обнаружения электронных данных будет выполняться в расположение вспомогательных.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="cc6b1-p108">Если роль руководитель или администратор eDiscovery для конкретной географически расположения, eDiscovery, руководитель или администратор будет только для выполнения действий поиска обнаружения электронных данных сайтов SharePoint и OneDrive сайтов, расположенных в этом географического расположения. Если eDiscovery Manager или администратор пытается сайты SharePoint или OneDrive за пределами указанной области поиска, результаты не будут возвращены. Кроме того при eDiscovery Manager или администратора для области экспорта, данные экспортируются Azure экземпляру этой области. Это позволяет организациям оставаться на соответствие требованиям, не позволяя содержимого для экспорта в охраняемых границы.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="cc6b1-141">Если это необходимо для обнаружения электронных данных диспетчера для поиска в нескольких регионах SharePoint, другой учетной записи пользователя будет необходимо создать для обнаружения электронных данных диспетчера, который определяет альтернативных регион, в котором размещены сайты SharePoint или OneDrive.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="cc6b1-142"><strong>Ферма с несколькими географически поддерживается географического расположения</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="cc6b1-143"><strong>обнаружение электронных данных для SharePoint экспортируемых данных будет находиться в это расположение данных больших двоичных объектов Azure...</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="cc6b1-144"><strong>ИМ</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="cc6b1-145">Центры обработки данных в США.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cc6b1-146"><strong>ЕВРО</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="cc6b1-147">Европа центров обработки данных</span><span class="sxs-lookup"><span data-stu-id="cc6b1-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cc6b1-148"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="cc6b1-149">Южно East или центров обработки данных Восточной Азии</span><span class="sxs-lookup"><span data-stu-id="cc6b1-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cc6b1-150"><strong>МОЖНО</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="cc6b1-151">Центры обработки данных в США.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cc6b1-152"><strong>СТАНДАРТНОЕ</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="cc6b1-153">Южно East или центров обработки данных Восточной Азии</span><span class="sxs-lookup"><span data-stu-id="cc6b1-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cc6b1-154"><strong>КОРЕЙСКИЙ</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="cc6b1-155">Расположение данных клиента по умолчанию</span><span class="sxs-lookup"><span data-stu-id="cc6b1-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cc6b1-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="cc6b1-157">Европа центров обработки данных</span><span class="sxs-lookup"><span data-stu-id="cc6b1-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cc6b1-158"><strong>ЯПОНСКИЙ</strong></span><span class="sxs-lookup"><span data-stu-id="cc6b1-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="cc6b1-159">Южно East или центров обработки данных Восточной Азии</span><span class="sxs-lookup"><span data-stu-id="cc6b1-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="cc6b1-160">Чтобы задать фильтр соответствия требованиям безопасности для области:</span><span class="sxs-lookup"><span data-stu-id="cc6b1-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="cc6b1-161">Открыть Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc6b1-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="cc6b1-162">ВВОД</span><span class="sxs-lookup"><span data-stu-id="cc6b1-162">Enter</span></span>  
    <span data-ttu-id="cc6b1-163">$s = New-PSSession - имя_конфигурации Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred — базовая проверка подлинности - AllowRedirection - SessionOption (New-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="cc6b1-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="cc6b1-164">$ = Import-PSSession $s - AllowClobber</span><span class="sxs-lookup"><span data-stu-id="cc6b1-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="cc6b1-165">**Новый ComplianceSecurityFilter** **-Действие** ВСЕ EnterTheNameYouWantToAssign **- FilterName** **-региона** EnterTheRegionParameter **-Пользователи** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="cc6b1-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="cc6b1-166">К примеру, **новые ComplianceSecurityFilter-действие** все NAMEDISCOVERYMANAGERS **- FilterName** **-региона** им **-Пользователи** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="cc6b1-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="cc6b1-167">В статье [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) Дополнительные параметры и синтаксис</span><span class="sxs-lookup"><span data-stu-id="cc6b1-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="cc6b1-168">Поиск в журнале аудита</span><span class="sxs-lookup"><span data-stu-id="cc6b1-168">Audit log search</span></span>

<span data-ttu-id="cc6b1-p109">Объединенные [журнал аудита](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) все географического расположения доступна на странице поиска журнала аудита Office 365. Можно просмотреть все записи журнала аудита из через geos, например им & ЕВРО географически пользовательских действий будет отображаться в одном представлении org и примените существующих фильтров для просмотра действий определенного пользователя.</span><span class="sxs-lookup"><span data-stu-id="cc6b1-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
