---
title: Настройка клиента OneDrive для бизнеса с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Сведения о настройке OneDrive для бизнеса с поддержкой нескольких регионов.
ms.openlocfilehash: 6c4a1012f3f26265ef88d82c55bb3ac11cc82da4
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849875"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="f33af-103">Настройка клиента OneDrive для бизнеса с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="f33af-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="f33af-p101">Прежде чем настраивать клиент OneDrive для бизнеса с поддержкой нескольких регионов, прочтите статью [Планирование использования OneDrive для бизнеса с поддержкой нескольких регионов](plan-for-multi-geo.md). Чтобы выполнить шаги, описанные в этой статье, вам понадобится список географических расположений, которые хотите включить в качестве периферийных расположений, а также группа тестовых пользователей, которых хотите подготовить к работе для этих расположений.</span><span class="sxs-lookup"><span data-stu-id="f33af-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="f33af-106">Добавление поддержки нескольких регионов в план Office 365 для клиента</span><span class="sxs-lookup"><span data-stu-id="f33af-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="f33af-p102">Чтобы можно было использовать OneDrive для бизнеса с поддержкой нескольких регионов, вам понадобится _план поддержки нескольких регионов в Office 365_. Вместе с сотрудниками, занимающимися учетными записями, добавьте этот план для клиента. Эти сотрудники свяжут вас с подходящим специалистом по лицензированию и помогут настроить клиент.</span><span class="sxs-lookup"><span data-stu-id="f33af-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="f33af-p103">Обратите внимание на то, что _план поддержки нескольких регионов в Office 365_ — это план обслуживания на уровне пользователя. Для каждого пользователя, которого нужно разместить в периферийном геообъекте, понадобится лицензия. Постепенно можно добавлять дополнительные лицензии по мере добавления пользователей в периферийные географические расположения.</span><span class="sxs-lookup"><span data-stu-id="f33af-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="f33af-113">Когда клиент будет подготовлен к работе с использованием _плана поддержки нескольких регионов в Office 365_, в [Центре администрирования OneDrive](https://admin.onedrive.com) станет доступной вкладка **Географические расположения**.</span><span class="sxs-lookup"><span data-stu-id="f33af-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="f33af-114">Добавление периферийных расположений к клиенту</span><span class="sxs-lookup"><span data-stu-id="f33af-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="f33af-p104">Для каждого географического расположения, в котором вы хотите использовать OneDrive для бизнеса, необходимо добавить периферийное расположение. Доступные географические расположения показаны в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="f33af-p104">You must add a satellite location for each geo location where you want to use OneDrive for Business. Available geo locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f33af-117"><strong>Расположение</strong></span><span class="sxs-lookup"><span data-stu-id="f33af-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="f33af-118"><strong>Код</strong></span><span class="sxs-lookup"><span data-stu-id="f33af-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f33af-119">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="f33af-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="f33af-120">APC</span><span class="sxs-lookup"><span data-stu-id="f33af-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f33af-121">Австралия</span><span class="sxs-lookup"><span data-stu-id="f33af-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="f33af-122">AUS</span><span class="sxs-lookup"><span data-stu-id="f33af-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f33af-123">Канада</span><span class="sxs-lookup"><span data-stu-id="f33af-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="f33af-124">CAN</span><span class="sxs-lookup"><span data-stu-id="f33af-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f33af-125">Европа, Ближний Восток и Африка</span><span class="sxs-lookup"><span data-stu-id="f33af-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="f33af-126">EUR</span><span class="sxs-lookup"><span data-stu-id="f33af-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f33af-127">Франция</span><span class="sxs-lookup"><span data-stu-id="f33af-127">France</span></span></td>
<td align="left"><span data-ttu-id="f33af-128">FRA</span><span class="sxs-lookup"><span data-stu-id="f33af-128">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f33af-129">Япония</span><span class="sxs-lookup"><span data-stu-id="f33af-129">Japan</span></span></td>
<td align="left"><span data-ttu-id="f33af-130">JPN</span><span class="sxs-lookup"><span data-stu-id="f33af-130">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f33af-131">Республика Корея</span><span class="sxs-lookup"><span data-stu-id="f33af-131">Korea</span></span></td>
<td align="left"><span data-ttu-id="f33af-132">KOR</span><span class="sxs-lookup"><span data-stu-id="f33af-132">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f33af-133">Северная Америка</span><span class="sxs-lookup"><span data-stu-id="f33af-133">North America</span></span></td>
<td align="left"><span data-ttu-id="f33af-134">NAM</span><span class="sxs-lookup"><span data-stu-id="f33af-134">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f33af-135">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="f33af-135">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="f33af-136">GBR</span><span class="sxs-lookup"><span data-stu-id="f33af-136">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f33af-137">Добавление периферийного расположения</span><span class="sxs-lookup"><span data-stu-id="f33af-137">To add a satellite geo location</span></span>

1. <span data-ttu-id="f33af-138">Откройте [Центр администрирования OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="f33af-138">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="f33af-139">Перейдите на вкладку **Географические расположения**.</span><span class="sxs-lookup"><span data-stu-id="f33af-139">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="f33af-140">Нажмите кнопку **Добавить расположение**.</span><span class="sxs-lookup"><span data-stu-id="f33af-140">Click **Add location**.</span></span>

4. <span data-ttu-id="f33af-141">Выберите нужное расположение и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="f33af-141">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="f33af-142">Укажите домен, который хотите использовать для географического расположения, и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="f33af-142">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="f33af-143">Нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="f33af-143">Click **Close**.</span></span>

<span data-ttu-id="f33af-p105">В зависимости от размера клиента подготовка к работе может занять от нескольких до 72 часов. Когда подготовка периферийного расположения завершится, вы получите подтверждающее электронное сообщение. Когда новое географическое расположение отобразится в синем цвете на карте вкладки **Географические расположения** в Центре администрирования OneDrive, вы сможете перейти к настройке предпочтительного расположения данных пользователей для этого географического расположения.</span><span class="sxs-lookup"><span data-stu-id="f33af-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="f33af-p106">Для нового периферийного расположения будут заданы параметры по умолчанию. Это позволит настроить его в соответствии с локальными требованиями.</span><span class="sxs-lookup"><span data-stu-id="f33af-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="f33af-149">Настройка предпочтительного расположения данных пользователей</span><span class="sxs-lookup"><span data-stu-id="f33af-149">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="f33af-p107">Настроив необходимые периферийные расположения данных, вы можете обновить учетные записи пользователей для применения соответствующих предпочтительных расположений данных. Рекомендуем задать предпочтительное расположение данных для каждого пользователя, даже если какие-то пользователи остаются в центральном расположении.</span><span class="sxs-lookup"><span data-stu-id="f33af-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="f33af-152">Прежде чем развертывать поддержку нескольких регионов для всей организации, рекомендуем начать проверки с вовлечением тестового пользователя или небольшой группы пользователей.</span><span class="sxs-lookup"><span data-stu-id="f33af-152">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="f33af-p108">В AAD существует два типа объектов пользователя: синхронизированные и только облачные. Следуйте соответствующим инструкциям для вашего типа пользователей.</span><span class="sxs-lookup"><span data-stu-id="f33af-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="f33af-155">Синхронизация предпочтительного расположения данных пользователя с помощью AD Connect</span><span class="sxs-lookup"><span data-stu-id="f33af-155">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="f33af-p109">Если пользователи вашей организации синхронизируются из системы локальной службы Active Directory в Azure Active Directory, соответствующий параметр PreferredDataLocation должен быть заполнен в AD и синхронизирован с AAD. Чтобы настроить синхронизацию предпочтительных расположений данных из локальной службы Active Directory в Azure Active Directory, следуйте инструкциям из статьи [Синхронизация Azure AD Connect: внесение изменений в конфигурацию по умолчанию](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration).</span><span class="sxs-lookup"><span data-stu-id="f33af-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="f33af-158">Рекомендуем включить настройку предпочтительного расположения данных пользователя в стандартный рабочий процесс создания пользователей.</span><span class="sxs-lookup"><span data-stu-id="f33af-158">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f33af-p110">В случае новых пользователей, для которых служба OneDrive не подготовлена к работе, следует подождать по крайней мере 24 часа после синхронизации PDL пользователя в Azure Active Directory. Это срок распространения изменений, по завершении которого пользователи смогут войти в OneDrive для бизнеса. (Настройка предпочтительного расположения данных до входа пользователя с целью подготовки к работе OneDrive для бизнеса позволяет обеспечить подготовку OneDrive в правильном расположении.)</span><span class="sxs-lookup"><span data-stu-id="f33af-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="f33af-161">Настройка предпочтительного расположения данных для облачных пользователей</span><span class="sxs-lookup"><span data-stu-id="f33af-161">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="f33af-162">Если пользователи вашей организации не синхронизируются из системы локальной службы Active Directory в Azure Active Directory, то есть создаются в Office 365 или Azure Active Directory, задать PDL нужно с помощью Azure Active Directory PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f33af-162">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="f33af-p111">Процедуры, описанные в этом разделе, требуют наличия [модуля Microsoft Azure Active Directory для Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Если вы уже установили Azure Active Directory PowerShell, нужно обновление до последней версии.</span><span class="sxs-lookup"><span data-stu-id="f33af-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="f33af-165">Откройте модуль Microsoft Azure Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f33af-165">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="f33af-166">Запустите командлет `Connect-MsolService` и введите учетные данные глобального администратора для своего клиента.</span><span class="sxs-lookup"><span data-stu-id="f33af-166">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="f33af-p112">Запустите командлет [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser), чтобы задать предпочтительное расположение данных для каждого из пользователей. Пример:</span><span class="sxs-lookup"><span data-stu-id="f33af-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="f33af-p113">Командлет Get-MsolUser позволяет проверить обновление предпочтительного расположения данных. Пример:</span><span class="sxs-lookup"><span data-stu-id="f33af-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="f33af-171">Рекомендуем включить настройку предпочтительного расположения данных пользователя в стандартный рабочий процесс создания пользователей.</span><span class="sxs-lookup"><span data-stu-id="f33af-171">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f33af-p114">В случае новых пользователей, для которых служба OneDrive не подготовлена к работе, следует подождать по крайней мере 24 часа после настройки PDL пользователя. Это срок распространения изменений, по завершении которого пользователи смогут войти в OneDrive. (Настройка предпочтительного расположения данных до входа пользователя с целью подготовки к работе OneDrive для бизнеса позволяет обеспечить подготовку OneDrive в правильном расположении.)</span><span class="sxs-lookup"><span data-stu-id="f33af-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="f33af-174">Подготовка к работе OneDrive и влияние PDL</span><span class="sxs-lookup"><span data-stu-id="f33af-174">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="f33af-p115">Если у пользователя уже есть сайт OneDrive, созданный в клиенте, при настройке его PDL не будет автоматически выполняться перемещение его OneDrive. Чтобы переместить OneDrive пользователя, см. статью [Перемещение OneDrive для бизнеса в отношении геообъекта](move-onedrive-between-geo-locations.md). Выполните инструкции из раздела о перемещении OneDrive из одного геообъекта в другой.</span><span class="sxs-lookup"><span data-stu-id="f33af-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="f33af-177">Если у пользователя нет сайта OneDrive в клиенте, для этого пользователя будет выполнена подготовка OneDrive к работе в соответствии со значением его PDL (при условии, что PDL пользователя соответствует одному из периферийных расположений компании.</span><span class="sxs-lookup"><span data-stu-id="f33af-177">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="f33af-178">Настройка поиска с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="f33af-178">Configuring Multi-Geo search</span></span>

<span data-ttu-id="f33af-179">Для клиента с несколькими регионами будет доступен поиск с объединением результатов, благодаря которому при отправке поискового запроса будут возвращаться данные из любого расположения клиента.</span><span class="sxs-lookup"><span data-stu-id="f33af-179">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="f33af-180">По умолчанию возвращаются объединенные результаты, даже когда каждый индекс поиска находится в пределах релевантного геообъекта, если поиск выполняется из этих точек входа:</span><span class="sxs-lookup"><span data-stu-id="f33af-180">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="f33af-181">OneDrive для бизнеса;</span><span class="sxs-lookup"><span data-stu-id="f33af-181">OneDrive for business</span></span>

- <span data-ttu-id="f33af-182">Delve;</span><span class="sxs-lookup"><span data-stu-id="f33af-182">Delve</span></span>

- <span data-ttu-id="f33af-183">домашняя страница SharePoint;</span><span class="sxs-lookup"><span data-stu-id="f33af-183">SharePoint Home</span></span>

- <span data-ttu-id="f33af-184">центр поиска.</span><span class="sxs-lookup"><span data-stu-id="f33af-184">Search Center</span></span>

<span data-ttu-id="f33af-185">Кроме этого, возможности поиска с поддержкой нескольких регионов можно настроить для специальных поисковых приложений, которые используют API поиска SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f33af-185">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="f33af-186">Ознакомьтесь со статьей [Настройка поиска в OneDrive для бизнеса с поддержкой нескольких регионов](configure-search-for-multi-geo.md), в которой изложены соответствующие инструкции, а также описаны ограничения и различия.</span><span class="sxs-lookup"><span data-stu-id="f33af-186">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="f33af-187">Проверка настройки OneDrive для бизнеса с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="f33af-187">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="f33af-p116">Ниже приведены некоторые основные варианты использования, которые можете включить в свой план проверки перед полным развертыванием OneDrive для бизнеса с поддержкой нескольких регионов в организации. Выполнив эти тесты и проработав дополнительные варианты использования, подходящие для вашей организации, можете перейти к добавлению пользователей в начальную пилотную группу.</span><span class="sxs-lookup"><span data-stu-id="f33af-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="f33af-190">**OneDrive для бизнеса**</span><span class="sxs-lookup"><span data-stu-id="f33af-190">**OneDrive for Business**</span></span>

<span data-ttu-id="f33af-p117">В средстве запуска приложений Office 365 выберите OneDrive и убедитесь, что вы автоматически направляетесь к соответствующему географическому расположению пользователя с учетом PDL пользователя. Теперь следует выполнить подготовку OneDrive для бизнеса в этом расположении. Когда подготовка будет завершена, попробуйте отправить и скачать несколько документов.</span><span class="sxs-lookup"><span data-stu-id="f33af-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="f33af-194">**Мобильное приложение OneDrive**</span><span class="sxs-lookup"><span data-stu-id="f33af-194">**OneDrive Mobile App**</span></span>

<span data-ttu-id="f33af-p118">Войдите в мобильное приложение OneDrive, используя тестовые учетные данные. Убедитесь, что файлы в OneDrive для бизнеса отображаются и вы можете с ними работать на мобильном устройстве.</span><span class="sxs-lookup"><span data-stu-id="f33af-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="f33af-197">**Клиент синхронизации OneDrive**</span><span class="sxs-lookup"><span data-stu-id="f33af-197">**OneDrive sync client**</span></span>

<span data-ttu-id="f33af-p119">Убедитесь в том, что клиент синхронизации OneDrive автоматически определяет географическое расположение OneDrive для бизнеса после входа. Если вам нужно скачать клиент синхронизации, в библиотеке OneDrive выберите **Синхронизация**.</span><span class="sxs-lookup"><span data-stu-id="f33af-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="f33af-200">**Приложения Office**</span><span class="sxs-lookup"><span data-stu-id="f33af-200">**Office applications**</span></span>

<span data-ttu-id="f33af-p120">Убедитесь, что можете войти в OneDrive для бизнеса из приложения Office, например Word. Откройте приложение Office и выберите "OneDrive – <TenantName>". Office обнаружит географическое расположение OneDrive и отобразит файлы, которые вы можете открыть.</span><span class="sxs-lookup"><span data-stu-id="f33af-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="f33af-204">**Общий доступ**</span><span class="sxs-lookup"><span data-stu-id="f33af-204">**Sharing**</span></span>

<span data-ttu-id="f33af-p121">Попробуйте предоставить доступ к файлам в OneDrive. Убедитесь в том, что средство выбора людей показывает вам всех пользователей SharePoint Online независимо от того, каковы их географические расположения.</span><span class="sxs-lookup"><span data-stu-id="f33af-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
