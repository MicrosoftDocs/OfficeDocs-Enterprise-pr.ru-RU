---
title: Администрирование среды с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Сведения об администрировании служб SharePoint и OneDrive в среде с поддержкой нескольких регионов.
ms.openlocfilehash: 12da695b44c5102c985a8d64960b1d20e092c8cd
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2018
ms.locfileid: "21550062"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="45370-103">Администрирование среды с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="45370-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="45370-104">Из этой статьи вы узнаете, как службы OneDrive и SharePoint работают в среде с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="45370-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="45370-105">Интерфейс администрирования OneDrive</span><span class="sxs-lookup"><span data-stu-id="45370-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="45370-p101">В [Центре администрирования OneDrive](https://admin.onedrive.com) есть вкладка **Географические расположения** в левой панели навигации, где представлена карта, на которой можно просматривать географические расположения и управлять ими. Эта страница используется для добавления и удаления географических расположений для клиента.</span><span class="sxs-lookup"><span data-stu-id="45370-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="45370-108">Таксономия</span><span class="sxs-lookup"><span data-stu-id="45370-108">Taxonomy</span></span>

<span data-ttu-id="45370-p102">Мы поддерживаем единую [таксономию](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) для управляемых корпоративных метаданных в разных географических расположениях, где главная копия находится в центральном расположении для компании. Рекомендуем управлять глобальной таксономией из центрального расположения и добавлять термины для определенных расположений только в таксономию географического расположения. Глобальные термины таксономии будут синхронизироваться со спутниковыми географическими расположениями.</span><span class="sxs-lookup"><span data-stu-id="45370-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="45370-112">Общий доступ</span><span class="sxs-lookup"><span data-stu-id="45370-112">Sharing</span></span>

<span data-ttu-id="45370-p103">Администраторы могут добавлять политики общего доступа и управлять ими для каждого из расположений. На сайтах OneDrive в каждом географическом расположении будут действовать только параметры общего доступа для соответствующего географического расположения. (Например, вы можете разрешить [внешний общий доступ](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) для центрального расположения, но не для спутникового, или наоборот.) Обратите внимание, что параметры общего доступа не позволяют настраивать ограничения доступа между разными географическими расположениями.</span><span class="sxs-lookup"><span data-stu-id="45370-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo-locations.</span></span>

<span data-ttu-id="45370-p104">В OneDrive с поддержкой нескольких регионов необходимо управлять параметрами общего доступа в каждом географическом расположении, так как они не синхронизируются в клиенте. Управлять общим доступом можно на странице [параметров общего доступа в Центре администрирования OneDrive](https://admin.onedrive.com/?v=SharingSettings). По умолчанию внешний доступ разрешен всем в каждом спутниковом расположении.</span><span class="sxs-lookup"><span data-stu-id="45370-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="45370-119">Приложение профилей пользователей</span><span class="sxs-lookup"><span data-stu-id="45370-119">User Profile Application</span></span>

<span data-ttu-id="45370-p105">В каждом географическом расположении есть [приложение профилей пользователей](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723). Данные профиля каждого пользователя хранятся в каждом географическом расположении и доступны администратору этого расположения.</span><span class="sxs-lookup"><span data-stu-id="45370-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="45370-p106">Если у вас есть настраиваемые свойства профиля, рекомендуем использовать одну и ту же схему профилей в разных регионах и заполнять настраиваемые свойства профиля либо во всех географических расположениях, либо там, где это необходимо. Для программного заполнения данных профиля пользователя используйте [API массового обновления профилей](https://docs.microsoft.com/ru-RU/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).</span><span class="sxs-lookup"><span data-stu-id="45370-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/ru-RU/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="45370-124">BCS, Secure Store, приложения</span><span class="sxs-lookup"><span data-stu-id="45370-124">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="45370-125">Для служб BCS, Secure Store и приложений есть отдельные экземпляры для разных регионов, поэтому администратор SharePoint Online должен управлять этими службами и настраивать их для каждого регионального экземпляра, где они должны присутствовать.</span><span class="sxs-lookup"><span data-stu-id="45370-125">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="45370-126">Центр администрирования безопасности и соответствия требованиям</span><span class="sxs-lookup"><span data-stu-id="45370-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="45370-127">Для клиента с поддержкой нескольких регионов используется один центральный центр соответствия требованиям — [Центр безопасности и соответствия требованиям Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="45370-127">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="45370-128">Политика защиты от потери данных (DLP) для службы Information Protection (IP)</span><span class="sxs-lookup"><span data-stu-id="45370-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="45370-p107">Вы можете настраивать политики IP DLP для OneDrive для бизнеса в Центре безопасности и соответствия требованиям, задавая нужную область действия политик для всего клиента или для всех соответствующих пользователей. Например, если вам нужно выбрать политику для пользователя OneDrive в спутниковом расположении, вы можете применить ее к определенной службе OneDrive и указать URL-адрес OneDrive пользователя. Общие рекомендации по созданию политик защиты от потери данных см. в статье [Обзор политик защиты от потери данных](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span><span class="sxs-lookup"><span data-stu-id="45370-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="45370-132">Политики защиты от потери данных автоматически синхронизируются в соответствии с их применимостью к каждому географическому расположению.</span><span class="sxs-lookup"><span data-stu-id="45370-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="45370-133">Реализовать службу Information Protection и политик защиты от потери данных для всех пользователей в определенном географическом расположении с помощью пользовательского интерфейса невозможно. Вместо этого необходимо выбрать применимые учетные данные OneDrive для политики или применить политику глобально для всех учетных записей OneDrive.</span><span class="sxs-lookup"><span data-stu-id="45370-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="45370-134">Обнаружение электронных данных</span><span class="sxs-lookup"><span data-stu-id="45370-134">eDiscovery</span></span> 

<span data-ttu-id="45370-p108">По умолчанию менеджер по обнаружению электронных данных или администратор в клиенте с поддержкой нескольких регионов сможет обнаруживать электронные данные только в центральном расположении для этого клиента. Чтобы обеспечить поддержку обнаружения электронных данных для спутниковых расположений, в PowerShell добавлен новый параметр Region для фильтра соответствия требованиям безопасности.</span><span class="sxs-lookup"><span data-stu-id="45370-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="45370-137">Глобальный администратор Office 365 должен предоставить менеджеру по обнаружению электронных данных право разрешать другим пользователям выполнять обнаружение электронных данных и назначать параметр Region в соответствующем фильтре соответствия требованиям безопасности, чтобы указывать спутниковое расположение в качестве региона для обнаружения электронных данных. В противном случае обнаружение электронных данных не будет выполняться для спутникового расположения.</span><span class="sxs-lookup"><span data-stu-id="45370-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="45370-p109">Если роль менеджера по обнаружению электронных данных или администратора задана для определенного географического расположения, то соответствующий пользователь сможет выполнять операции поиска с обнаружением электронных данных только на сайтах SharePoint и OneDrive, расположенных в этом регионе. Если менеджер по обнаружению электронных данных попробует выполнить поиск на сайтах SharePoint или OneDrive за пределами указанного региона, результаты не будут возвращаться. Кроме того, когда менеджер по обнаружению электронных данных или администратор для региона запускает экспорт, данные экспортируются в экземпляр Azure в этом регионе. Это помогает организациям обеспечивать соответствие требованиям, не разрешая экспорт контента через контролируемые границы.</span><span class="sxs-lookup"><span data-stu-id="45370-p109">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="45370-142">Если менеджеру по обнаружению электронных данных требуется искать контент в нескольких регионах SharePoint, необходимо создать для него еще одну учетную запись, указывающую альтернативный регион, где находятся сайты OneDrive или SharePoint.</span><span class="sxs-lookup"><span data-stu-id="45370-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="45370-143"><strong>Географические расположения с поддержкой нескольких регионов</strong></span><span class="sxs-lookup"><span data-stu-id="45370-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="45370-144"><strong>Расположение больших двоичных объектов Azure, в котором будет выполняться обнаружение электронных данных, экспортированных из SharePoint</strong></span><span class="sxs-lookup"><span data-stu-id="45370-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="45370-145"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="45370-145"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="45370-146">Центры обработки данных в Юго-Восточной или Восточной Азии</span><span class="sxs-lookup"><span data-stu-id="45370-146">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="45370-147"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="45370-147"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="45370-148">Центры обработки данных в Юго-Восточной или Восточной Азии</span><span class="sxs-lookup"><span data-stu-id="45370-148">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="45370-149"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="45370-149"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="45370-150">Центры обработки данных в США</span><span class="sxs-lookup"><span data-stu-id="45370-150">US datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="45370-151"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="45370-151"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="45370-152">Центры обработки данных в Европе</span><span class="sxs-lookup"><span data-stu-id="45370-152">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="45370-153"><strong>FRA</strong></span><span class="sxs-lookup"><span data-stu-id="45370-153"><strong>FRA</strong></span></span></td>
<td align="left"><span data-ttu-id="45370-154">Центры обработки данных в Европе</span><span class="sxs-lookup"><span data-stu-id="45370-154">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="45370-155"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="45370-155"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="45370-156">Центры обработки данных в Европе</span><span class="sxs-lookup"><span data-stu-id="45370-156">Europe datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="45370-157"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="45370-157"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="45370-158">Центры обработки данных в Юго-Восточной или Восточной Азии</span><span class="sxs-lookup"><span data-stu-id="45370-158">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="45370-159"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="45370-159"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="45370-160">Центры обработки данных в Юго-Восточной или Восточной Азии</span><span class="sxs-lookup"><span data-stu-id="45370-160">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="45370-161"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="45370-161"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="45370-162">Центры обработки данных в США</span><span class="sxs-lookup"><span data-stu-id="45370-162">US datacenters</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="45370-163">Установка фильтра соответствия требованиям безопасности для региона:</span><span class="sxs-lookup"><span data-stu-id="45370-163">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="45370-164">Откройте Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="45370-164">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="45370-165">Введите следующие команды:</span><span class="sxs-lookup"><span data-stu-id="45370-165">Enter</span></span>  
    <span data-ttu-id="45370-166">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="45370-166">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="45370-167">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="45370-167">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="45370-168">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** Введите_нужное_имя **-Region** Введите_параметр_региона **-Users** Введите_имя_субъекта-пользователя</span><span class="sxs-lookup"><span data-stu-id="45370-168">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="45370-169">Пример: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="45370-169">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="45370-170">Дополнительные параметры и синтаксис рассматриваются в статье [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx).</span><span class="sxs-lookup"><span data-stu-id="45370-170">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="45370-171">Поиск в журнале аудита</span><span class="sxs-lookup"><span data-stu-id="45370-171">Audit log search</span></span>

<span data-ttu-id="45370-p110">Единый [журнал аудита](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) для всех географических расположений доступен на странице поиска в журнале аудита Office 365. Вы можете просматривать все записи журнала аудита из всех регионов. Например, действия пользователей из регионов NAM и EUR отображаются в одном организационном представлении, после чего вы можете применять существующие фильтры для просмотра действий определенного пользователя.</span><span class="sxs-lookup"><span data-stu-id="45370-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
