---
title: OneDrive для конфигурации несколькими бизнес-географически клиентов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Сведения о настройке OneDrive для бизнеса Multi-географически.
ms.openlocfilehash: 56268acd319684ecb713e674b8accbe311d08dce
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="0b78f-103">OneDrive для конфигурации несколькими бизнес-географически клиентов</span><span class="sxs-lookup"><span data-stu-id="0b78f-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="0b78f-p101">Перед настройкой вашего клиента для OneDrive для бизнеса Multi-географически убедитесь, что вы прочли [Планирование использования службы OneDrive для бизнеса Multi-географически](plan-for-multi-geo.md). Для выполнения действия, описанные в этой статье, вам потребуются список расположений, которые необходимо включить и тестовых пользователей, которые необходимо подготовить для этих папок.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="0b78f-106">Добавление возможности несколькими географически в плане Office 365 к клиенту</span><span class="sxs-lookup"><span data-stu-id="0b78f-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="0b78f-p102">Для использования OneDrive для бизнеса Multi-географически, требуется план _Несколькими географически возможности в Office 365_ . Работа с учетной записи группы с просьбой добавить этот план к клиенту. Ваша группа учетной записи будет подключение вы с соответствующие специалиста по лицензированию и получение вашего клиента настроены.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="0b78f-p103">Обратите внимание, что план _Несколькими географически возможности в Office 365_ план обслуживания уровня пользователя. Требуется лицензия для каждого пользователя, который будет размещаться в расположении вспомогательная. Можно добавить дополнительные лицензии по времени по мере добавления пользователей в расположение вспомогательных.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="0b78f-113">После вашего клиента был подготовлен с _Несколькими географически возможности в Office 365_ плана, на вкладке **географического расположения** будут доступны в [центре администрирования OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="0b78f-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="0b78f-114">Настройка разрешенных данных расположения (ADL) к клиенту</span><span class="sxs-lookup"><span data-stu-id="0b78f-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="0b78f-p104">Допустимое расположение данных необходимо задать для SharePoint для каждого географического расположения которых вы собираетесь использовать OneDrive для бизнеса. В следующей таблице показаны доступные географически расположений:</span><span class="sxs-lookup"><span data-stu-id="0b78f-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="0b78f-117"><strong>Расположение</strong></span><span class="sxs-lookup"><span data-stu-id="0b78f-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="0b78f-118"><strong>Код</strong></span><span class="sxs-lookup"><span data-stu-id="0b78f-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="0b78f-119">Северная Америка</span><span class="sxs-lookup"><span data-stu-id="0b78f-119">North America</span></span></td>
<td align="left"><span data-ttu-id="0b78f-120">ИМ</span><span class="sxs-lookup"><span data-stu-id="0b78f-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0b78f-121">Европа / Средний Восток и Африка</span><span class="sxs-lookup"><span data-stu-id="0b78f-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="0b78f-122">ЕВРО</span><span class="sxs-lookup"><span data-stu-id="0b78f-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0b78f-123">Азиатско-Тихоокеанский регион</span><span class="sxs-lookup"><span data-stu-id="0b78f-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="0b78f-124">APC</span><span class="sxs-lookup"><span data-stu-id="0b78f-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0b78f-125">Австралия</span><span class="sxs-lookup"><span data-stu-id="0b78f-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="0b78f-126">СТАНДАРТНОЕ</span><span class="sxs-lookup"><span data-stu-id="0b78f-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0b78f-127">Япония</span><span class="sxs-lookup"><span data-stu-id="0b78f-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="0b78f-128">ЯПОНСКИЙ</span><span class="sxs-lookup"><span data-stu-id="0b78f-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0b78f-129">Канада</span><span class="sxs-lookup"><span data-stu-id="0b78f-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="0b78f-130">МОЖНО</span><span class="sxs-lookup"><span data-stu-id="0b78f-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0b78f-131">Соединенное Королевство</span><span class="sxs-lookup"><span data-stu-id="0b78f-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="0b78f-132">GBR</span><span class="sxs-lookup"><span data-stu-id="0b78f-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0b78f-133">Корея</span><span class="sxs-lookup"><span data-stu-id="0b78f-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="0b78f-134">КОРЕЙСКИЙ</span><span class="sxs-lookup"><span data-stu-id="0b78f-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="0b78f-135">Чтобы добавить расположение вспомогательных географически</span><span class="sxs-lookup"><span data-stu-id="0b78f-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="0b78f-136">Откройте [Центр администрирования OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="0b78f-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="0b78f-137">Перейдите на вкладку **географического расположения** .</span><span class="sxs-lookup"><span data-stu-id="0b78f-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="0b78f-138">Нажмите кнопку **Добавить расположения**.</span><span class="sxs-lookup"><span data-stu-id="0b78f-138">Click **Add location**.</span></span>

4. <span data-ttu-id="0b78f-139">Выберите папку, где вы хотите добавить и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="0b78f-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="0b78f-140">Введите имя домена, который будет использоваться вместе с географического расположения и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="0b78f-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="0b78f-141">Щелкните **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="0b78f-141">Click **Close**.</span></span>

<span data-ttu-id="0b78f-p105">Подготовка может занять от нескольких часов до 72 часов, в зависимости от размера вашего клиента. После завершения подготовки расположение вспомогательных будет отправлено сообщение электронной почты. При появлении в новом расположении географически синего цвета на карте на вкладке **географического расположения** в центре администрирования OneDrive можно перейти к задать расположение предпочитаемый данных пользователей, географического расположения.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="0b78f-p106">Новые расположения географически вспомогательных будет настраиваться с параметрами по умолчанию. Это позволит настроить эту папку geo в зависимости от локального соответствие требованиям.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="0b78f-147">Расположение данных предпочитаемый параметр пользователей</span><span class="sxs-lookup"><span data-stu-id="0b78f-147">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="0b78f-p107">После включения расположения необходимые данные можно обновить учетные записи пользователей для использования расположение соответствующих данных. Рекомендуется задавать расположение предпочитаемый данных для каждого пользователя, даже в том случае, если пользователь остаются в расположение данных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="0b78f-150">Рекомендуется начать проверки с помощью тестового пользователя или небольшой группы пользователей до развертывания системы несколькими географически возможности для более широкой организации.</span><span class="sxs-lookup"><span data-stu-id="0b78f-150">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="0b78f-p108">В AAD существует два типа объектов-пользователей: только пользователей и синхронизированных пользователей в облаке. Выполните соответствующие инструкции для соответствующего типа пользователя.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="0b78f-153">Синхронизация папки предпочитаемое данных пользователя, с помощью AD Connect</span><span class="sxs-lookup"><span data-stu-id="0b78f-153">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="0b78f-p109">Если пользователи вашей компании синхронизируются из Active Directory (AD) в локальной системе для Azure Active Directory (AAD), их PreferredDataLocation должен заполняться в AD и синхронизируются с AAD. Следуйте указаниям в [Azure AD подключение синхронизации: внести изменения в конфигурацию по умолчанию](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) Настройка предпочтительное расположение данных синхронизации локальной AD для AAD.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="0b78f-156">Рекомендуется включить параметр пользователя предпочтительный расположение данных в рамках рабочего процесса создания обычного пользователя.</span><span class="sxs-lookup"><span data-stu-id="0b78f-156">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b78f-p110">Для новых пользователей с помощью не подготовлен OneDrive через менее 24 часа после PDL пользователя синхронизируется AAD изменения для распространения до входа пользователя onedrive для бизнеса. (Установка предпочитаемый данных расположения, прежде чем пользователь входит в целях подготовки их OneDrive для бизнеса гарантирует, что будет выполнена подготовка OneDrive нового пользователя в правильном месте.)</span><span class="sxs-lookup"><span data-stu-id="0b78f-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="0b78f-159">Параметр предпочитаемое расположение данных для облачных только пользователи</span><span class="sxs-lookup"><span data-stu-id="0b78f-159">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="0b78f-160">Если пользователи вашей компании не синхронизируются из Active Directory (AD) в локальной системе для Azure Active Directory (AAD), что означает, что они созданы в Office 365 или AAD, затем PDL должно иметь значение с помощью AAD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b78f-160">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="0b78f-p111">Процедуры, описанные в этом разделе требуется [Microsoft Azure Active Directory для Windows PowerShell модуле](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Если уже установлены AAD PowerShell, убедитесь, что обновление до последней версии.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="0b78f-163">Откройте модуль Microsoft Azure Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b78f-163">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="0b78f-164">Запустите `Connect-MsolService` и введите учетные данные глобального администратора для клиента.</span><span class="sxs-lookup"><span data-stu-id="0b78f-164">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="0b78f-p112">Командлет [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) задать расположение предпочитаемый данных для каждого пользователя. Например:</span><span class="sxs-lookup"><span data-stu-id="0b78f-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="0b78f-p113">Вы можете проверить, чтобы убедиться, что расположение предпочитаемый данных был обновлен должным образом с помощью командлета Get-MsolUser. Например:</span><span class="sxs-lookup"><span data-stu-id="0b78f-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="0b78f-169">Рекомендуется включить параметр пользователя предпочтительный расположение данных в рамках рабочего процесса создания обычного пользователя.</span><span class="sxs-lookup"><span data-stu-id="0b78f-169">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b78f-p114">Для новых пользователей с помощью не подготовлен OneDrive через менее 24 часа после задать PDL пользователя для изменения для распространения до входа пользователя в систему SharePoint OneDrive. (Установка предпочитаемый данных расположения, прежде чем пользователь входит в целях подготовки их OneDrive для бизнеса гарантирует, что будет выполнена подготовка OneDrive нового пользователя в правильном месте.)</span><span class="sxs-lookup"><span data-stu-id="0b78f-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="0b78f-172">Подготовка OneDrive и влияние PDL</span><span class="sxs-lookup"><span data-stu-id="0b78f-172">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="0b78f-p115">Если пользователь уже имеет OneDrive сайтов, созданных в клиентов, установка их PDL не будут перемещены автоматически их существующих OneDrive. Чтобы переместить пользователя OneDrive, обратитесь к разделу [OneDrive for Business географически перемещение](move-onedrive-between-geo-locations.md) следуйте инструкциям в OneDrive перемещение между различными расположениями географически.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="0b78f-175">Если пользователь не имеет сайта OneDrive в рамках клиента, OneDrive будет выполнена подготовка для них в соответствии с их значение PDL при условии, что PDL для пользователя соответствует одной из расположения допустимых данных компании (ADLs).</span><span class="sxs-lookup"><span data-stu-id="0b78f-175">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="0b78f-176">Настройка нескольких географически поиска</span><span class="sxs-lookup"><span data-stu-id="0b78f-176">Configuring Multi-Geo search</span></span>

<span data-ttu-id="0b78f-177">Клиенту несколькими географически будут иметь возможности сбору статистических данных поиска, позволяя поискового запроса для возвращения результатов в любом месте внутри клиента.</span><span class="sxs-lookup"><span data-stu-id="0b78f-177">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="0b78f-178">По умолчанию поиска из этих точек входа возвращает статистических данных, несмотря на то, что каждый индекс поиска находится в его расположения соответствующих географически:</span><span class="sxs-lookup"><span data-stu-id="0b78f-178">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="0b78f-179">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="0b78f-179">OneDrive for business</span></span>

- <span data-ttu-id="0b78f-180">Delve</span><span class="sxs-lookup"><span data-stu-id="0b78f-180">Delve</span></span>

- <span data-ttu-id="0b78f-181">Домашняя страница SharePoint</span><span class="sxs-lookup"><span data-stu-id="0b78f-181">SharePoint Home</span></span>

- <span data-ttu-id="0b78f-182">Центр поиска</span><span class="sxs-lookup"><span data-stu-id="0b78f-182">Search Center</span></span>

<span data-ttu-id="0b78f-183">Кроме того можно настроить несколькими географически возможности поиска для настраиваемого поиска приложений, использующих API поиска SharePoint.</span><span class="sxs-lookup"><span data-stu-id="0b78f-183">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="0b78f-184">Просмотрите [Настройка поиска для OneDrive для бизнеса Multi-географически](configure-search-for-multi-geo.md) инструкции, включая любые ограничения и отличия.</span><span class="sxs-lookup"><span data-stu-id="0b78f-184">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="0b78f-185">Проверка OneDrive для бизнеса Multi-географическая конфигурация</span><span class="sxs-lookup"><span data-stu-id="0b78f-185">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="0b78f-p116">Ниже приведены некоторые основные варианты, вы можете включить в плане проверки до широко развертывания системы OneDrive для бизнеса Multi-географически для вашей компании. После выполнения этих тестов и любые дополнительные варианты, относящиеся к вашей компании, можно перейти к добавления пользователей в начальное пилотной группы.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="0b78f-188">**OneDrive для бизнеса**</span><span class="sxs-lookup"><span data-stu-id="0b78f-188">**OneDrive for Business**</span></span>

<span data-ttu-id="0b78f-p117">Выберите элемент OneDrive от запуска приложения для Office 365 и убедитесь, что вы автоматически перенаправлены на соответствующие географического расположения для пользователей по PDL пользователя. OneDrive для бизнеса следует начинать подготовку в этом расположении. После предоставления try отправку и загрузку некоторые документы.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="0b78f-192">**OneDrive мобильного приложения**</span><span class="sxs-lookup"><span data-stu-id="0b78f-192">**OneDrive Mobile App**</span></span>

<span data-ttu-id="0b78f-p118">Войдите в приложении OneDrive мобильных устройств с помощью свои учетные данные тестирования. Убедитесь, что могут видеть ваше файлы OneDrive для бизнеса и может взаимодействовать с ними с мобильного устройства.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="0b78f-195">**Клиент синхронизации OneDrive**</span><span class="sxs-lookup"><span data-stu-id="0b78f-195">**OneDrive sync client**</span></span>

<span data-ttu-id="0b78f-p119">Убедитесь, что клиента синхронизации OneDrive автоматически обнаруживает OneDrive для географического расположения Business при выполнении входа. Если необходимо загрузить клиент синхронизации можно щелкнуть **синхронизации** в библиотеке OneDrive.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="0b78f-198">**Приложения Office**</span><span class="sxs-lookup"><span data-stu-id="0b78f-198">**Office applications**</span></span>

<span data-ttu-id="0b78f-p120">Убедитесь, что можно получить доступ к OneDrive для бизнеса, войдя из приложения Office, таких как Word. Откройте Office приложения и выберите пункт «OneDrive – <TenantName>«. Office определяет расположение OneDrive и отображение файлов, которые можно открыть.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="0b78f-202">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="0b78f-202">**Sharing**</span></span>

<span data-ttu-id="0b78f-p121">Попробуйте совместное использование файлов OneDrive. Убедитесь, что "Выбор людей" отображается всех SharePoint online пользователей независимо от их географического расположения.</span><span class="sxs-lookup"><span data-stu-id="0b78f-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
