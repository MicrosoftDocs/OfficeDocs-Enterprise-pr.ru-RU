---
title: Конфигурация клиента Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Сведения о настройке Microsoft 365 Multi-Geo.
ms.openlocfilehash: 928033dcbec0ad0b52f24bd0bec4dd6b9f9331bc
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052572"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a><span data-ttu-id="c0d29-103">Конфигурация клиента Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="c0d29-103">Microsoft 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="c0d29-104">Прежде чем настраивать клиент Microsoft 365 Multi-Geo, прочтите статью [План для Microsoft 365 Multi-Geo](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="c0d29-104">Before you configure your tenant for Microsoft 365 Multi-Geo, be sure you have read [Plan for Microsoft 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="c0d29-105">Чтобы выполнить шаги, описанные в этой статье, вам понадобится список географических расположений, которые нужно включить в качестве периферийных расположений, а также тестовые пользователи, которых нужно подготовить к работе для этих расположений.</span><span class="sxs-lookup"><span data-stu-id="c0d29-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a><span data-ttu-id="c0d29-106">Добавление поддержки нескольких регионов в план Microsoft 365 для клиента</span><span class="sxs-lookup"><span data-stu-id="c0d29-106">Add the Multi-Geo Capabilities in your Microsoft 365 plan to your tenant</span></span>

<span data-ttu-id="c0d29-107">Чтобы использовать Microsoft 365 Multi-Geo, вам понадобится план _поддержки нескольких регионов в Microsoft 365_.</span><span class="sxs-lookup"><span data-stu-id="c0d29-107">To use Microsoft 365 Multi-Geo, you need the _Multi-Geo Capabilities in Microsoft 365_ plan.</span></span> <span data-ttu-id="c0d29-108">Вместе с сотрудниками, занимающимися учетными записями, добавьте этот план для клиента.</span><span class="sxs-lookup"><span data-stu-id="c0d29-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="c0d29-109">Эти сотрудники свяжут вас с подходящим специалистом по лицензированию и помогут настроить клиент.</span><span class="sxs-lookup"><span data-stu-id="c0d29-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="c0d29-110">Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan.</span><span class="sxs-lookup"><span data-stu-id="c0d29-110">Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan.</span></span> <span data-ttu-id="c0d29-111">You need a license for each user that you want to host in a satellite location.</span><span class="sxs-lookup"><span data-stu-id="c0d29-111">You need a license for each user that you want to host in a satellite location.</span></span> <span data-ttu-id="c0d29-112">You can add more licenses over time as you add users in satellite locations.</span><span class="sxs-lookup"><span data-stu-id="c0d29-112">You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="c0d29-113">Когда клиент будет подготовлен к работе с планом _поддержки нескольких регионов в Microsoft 365_, в Центрах администрирования OneDrive и SharePoint станет доступной вкладка **Географические расположения**.</span><span class="sxs-lookup"><span data-stu-id="c0d29-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Microsoft 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="c0d29-114">Добавление периферийных расположений к клиенту</span><span class="sxs-lookup"><span data-stu-id="c0d29-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="c0d29-115">Для каждого географического расположения, в котором нужно хранить данные, необходимо добавить периферийное расположение.</span><span class="sxs-lookup"><span data-stu-id="c0d29-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="c0d29-116">Доступные географические расположения показаны в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="c0d29-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Снимок экрана: страница географических расположений в Центре администрирования SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="c0d29-118">Добавление периферийного расположения</span><span class="sxs-lookup"><span data-stu-id="c0d29-118">To add a satellite location</span></span>

1. <span data-ttu-id="c0d29-119">Откройте Центр администрирования SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c0d29-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="c0d29-120">Перейдите на вкладку **Географические расположения**.</span><span class="sxs-lookup"><span data-stu-id="c0d29-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="c0d29-121">Нажмите кнопку **Добавить расположение**.</span><span class="sxs-lookup"><span data-stu-id="c0d29-121">Click **Add location**.</span></span>

4. <span data-ttu-id="c0d29-122">Выберите нужное расположение и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="c0d29-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="c0d29-123">Укажите домен, который хотите использовать для географического расположения, и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="c0d29-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="c0d29-124">Нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="c0d29-124">Click **Close**.</span></span>

<span data-ttu-id="c0d29-125">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant.</span><span class="sxs-lookup"><span data-stu-id="c0d29-125">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant.</span></span> <span data-ttu-id="c0d29-126">Once provisioning of a satellite location has completed, you will receive an email confirmation.</span><span class="sxs-lookup"><span data-stu-id="c0d29-126">Once provisioning of a satellite location has completed, you will receive an email confirmation.</span></span> <span data-ttu-id="c0d29-127">When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span><span class="sxs-lookup"><span data-stu-id="c0d29-127">When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="c0d29-128">Your new satellite location will be set up with default settings.</span><span class="sxs-lookup"><span data-stu-id="c0d29-128">Your new satellite location will be set up with default settings.</span></span> <span data-ttu-id="c0d29-129">This will allow you to configure that satellite location as appropriate for your local compliance needs.</span><span class="sxs-lookup"><span data-stu-id="c0d29-129">This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="c0d29-130">Настройка предпочтительного расположения данных пользователей</span><span class="sxs-lookup"><span data-stu-id="c0d29-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="c0d29-131">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location.</span><span class="sxs-lookup"><span data-stu-id="c0d29-131">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location.</span></span> <span data-ttu-id="c0d29-132">We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span><span class="sxs-lookup"><span data-stu-id="c0d29-132">We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0d29-133">Если для предпочтительного расположения данных пользователя задано расположение, не настроенное в качестве периферийного или центрального, система по умолчанию использует центральное расположение при подготовке сайтов OneDrive и SharePoint, а также почтовых ящиков групп.</span><span class="sxs-lookup"><span data-stu-id="c0d29-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="c0d29-134">Прежде чем развертывать поддержку нескольких регионов для всей организации, рекомендуем начать проверки с вовлечением тестового пользователя или небольшой группы пользователей.</span><span class="sxs-lookup"><span data-stu-id="c0d29-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="c0d29-135">В Azure Active Directory (Azure AD) существует два типа объектов пользователя: синхронизированные и только облачные.</span><span class="sxs-lookup"><span data-stu-id="c0d29-135">In Azure Active Directory (Azure AD) there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="c0d29-136">Следуйте соответствующим инструкциям для вашего типа пользователей.</span><span class="sxs-lookup"><span data-stu-id="c0d29-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a><span data-ttu-id="c0d29-137">Синхронизация предпочтительного расположения данных пользователя с помощью Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="c0d29-137">Synchronize user's Preferred Data Location using Azure AD Connect</span></span> 

<span data-ttu-id="c0d29-138">Если пользователи вашей организации синхронизируются с Azure AD из локальной системы Active Directory, PreferredDataLocation заполняется в AD и синхронизируется с Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c0d29-138">If your company’s users are synchronized from an on-premises Active Directory system to Azure AD, their PreferredDataLocation must be populated in AD and synchronized to Azure AD.</span></span>

<span data-ttu-id="c0d29-139">Выполните действия, описанные в разделе [Синхронизация Azure Active Directory Connect: настройка предпочтительного расположения данных для ресурсов Microsoft 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation), чтобы настроить синхронизацию предпочтительного расположения данных с Azure AD из локальных доменных служб Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="c0d29-139">Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Microsoft 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from your on-premises Active Directory Domain Services (AD DS) to Azure AD.</span></span>

<span data-ttu-id="c0d29-140">Рекомендуем включить настройку предпочтительного расположения данных пользователя в стандартный рабочий процесс создания пользователей.</span><span class="sxs-lookup"><span data-stu-id="c0d29-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0d29-141">В случае новых пользователей, для которых служба OneDrive не подготовлена к работе, следует подождать по крайней мере 24 часа после синхронизации PDL пользователя с Azure AD. Это срок распространения изменений, по завершении которого пользователи смогут войти в OneDrive для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="c0d29-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure AD for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="c0d29-142">(Настройка предпочтительного расположения данных до входа пользователя с целью подготовки к работе OneDrive для бизнеса позволяет обеспечить подготовку OneDrive в правильном расположении.)</span><span class="sxs-lookup"><span data-stu-id="c0d29-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="c0d29-143">Настройка предпочтительного расположения данных для облачных пользователей</span><span class="sxs-lookup"><span data-stu-id="c0d29-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="c0d29-144">Если пользователи вашей организации не синхронизируются с Azure AD из локальной системы Active Directory, то есть создаются в Microsoft 365 или Azure AD, тогда PDL задается с помощью модуля Microsoft Azure Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0d29-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure AD, meaning they are created in Microsoft 365 or Azure AD, then the PDL must be set using the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="c0d29-145">Для выполнения процедур, описанных в этом разделе, требуется [Модуль Azure Active Directory для Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0).</span><span class="sxs-lookup"><span data-stu-id="c0d29-145">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0).</span></span> <span data-ttu-id="c0d29-146">Если у вас уже установлен этот модуль, убедитесь, что он обновлен до последней версии.</span><span class="sxs-lookup"><span data-stu-id="c0d29-146">If you already have this module installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="c0d29-147">[Подключитесь и выполните вход](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) с помощью набора учетных данных глобального администратора для вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="c0d29-147">[Connect and sign in](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) with a set of global administrator credentials for your tenant.</span></span>

2.  <span data-ttu-id="c0d29-148">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users.</span><span class="sxs-lookup"><span data-stu-id="c0d29-148">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users.</span></span> <span data-ttu-id="c0d29-149">For example:</span><span class="sxs-lookup"><span data-stu-id="c0d29-149">For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="c0d29-150">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0d29-150">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet.</span></span> <span data-ttu-id="c0d29-151">For example:</span><span class="sxs-lookup"><span data-stu-id="c0d29-151">For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Снимок экрана: окно PowerShell с командлетом set-msoluser](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="c0d29-153">Рекомендуем включить настройку предпочтительного расположения данных пользователя в стандартный рабочий процесс создания пользователей.</span><span class="sxs-lookup"><span data-stu-id="c0d29-153">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0d29-154">В случае новых пользователей, для которых служба OneDrive не подготовлена к работе, следует подождать по крайней мере 24 часа после настройки PDL пользователя. Это срок распространения изменений, по завершении которого пользователи смогут войти в OneDrive.</span><span class="sxs-lookup"><span data-stu-id="c0d29-154">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="c0d29-155">(Настройка предпочтительного расположения данных до входа пользователя с целью подготовки к работе OneDrive для бизнеса позволяет обеспечить подготовку OneDrive в правильном расположении.)</span><span class="sxs-lookup"><span data-stu-id="c0d29-155">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="c0d29-156">Подготовка к работе OneDrive и влияние PDL</span><span class="sxs-lookup"><span data-stu-id="c0d29-156">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="c0d29-157">Если у пользователя уже есть сайт OneDrive, созданный в клиенте, при настройке его PDL не будет автоматически выполняться перемещение его сайта OneDrive.</span><span class="sxs-lookup"><span data-stu-id="c0d29-157">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="c0d29-158">Чтобы переместить сайт OneDrive пользователя, см. статью [Перемещение OneDrive для бизнеса в отношении геообъекта](move-onedrive-between-geo-locations.md). Выполните инструкции из раздела о перемещении OneDrive из одного геообъекта в другой.</span><span class="sxs-lookup"><span data-stu-id="c0d29-158">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="c0d29-159">(Обратите внимание, что почтовый ящик Exchange пользователя не перемещается автоматически при настройке PDL пользователя.)</span><span class="sxs-lookup"><span data-stu-id="c0d29-159">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="c0d29-160">Если у пользователя нет сайта OneDrive в клиенте, для этого пользователя будет выполнена подготовка OneDrive к работе в соответствии со значением его PDL (при условии, что PDL пользователя соответствует одному из периферийных расположений компании).</span><span class="sxs-lookup"><span data-stu-id="c0d29-160">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="c0d29-161">Настройка поиска с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="c0d29-161">Configuring Multi-Geo search</span></span>

<span data-ttu-id="c0d29-162">Для клиента с несколькими регионами будет доступен поиск с объединением результатов, благодаря которому при отправке поискового запроса будут возвращаться данные из любого расположения клиента.</span><span class="sxs-lookup"><span data-stu-id="c0d29-162">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="c0d29-163">По умолчанию возвращаются объединенные результаты, даже когда каждый индекс поиска находится в пределах релевантного геообъекта, если поиск выполняется из этих точек входа:</span><span class="sxs-lookup"><span data-stu-id="c0d29-163">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="c0d29-164">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="c0d29-164">OneDrive for Business</span></span>

- <span data-ttu-id="c0d29-165">Delve;</span><span class="sxs-lookup"><span data-stu-id="c0d29-165">Delve</span></span>

- <span data-ttu-id="c0d29-166">домашняя страница SharePoint;</span><span class="sxs-lookup"><span data-stu-id="c0d29-166">SharePoint Home</span></span>

- <span data-ttu-id="c0d29-167">центр поиска.</span><span class="sxs-lookup"><span data-stu-id="c0d29-167">Search Center</span></span>

<span data-ttu-id="c0d29-168">Кроме этого, возможности поиска с поддержкой нескольких регионов можно настроить для специальных поисковых приложений, которые используют API поиска SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c0d29-168">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="c0d29-169">Ознакомьтесь со статьей [Настройка поиска в OneDrive для бизнеса с поддержкой нескольких регионов](configure-search-for-multi-geo.md), в которой изложены соответствующие инструкции, а также описаны ограничения и различия.</span><span class="sxs-lookup"><span data-stu-id="c0d29-169">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a><span data-ttu-id="c0d29-170">Проверка конфигурации Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="c0d29-170">Validating the Microsoft 365 Multi-Geo configuration</span></span>

<span data-ttu-id="c0d29-171">Ниже приведены некоторые основные варианты использования, которые можно включить в свой план проверки перед полным развертыванием Microsoft 365 Multi-Geo в организации.</span><span class="sxs-lookup"><span data-stu-id="c0d29-171">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Microsoft 365 Multi-Geo to your company.</span></span> <span data-ttu-id="c0d29-172">Выполнив эти тесты и проработав дополнительные варианты использования, подходящие для вашей организации, можно перейти к добавлению пользователей в начальную пилотную группу.</span><span class="sxs-lookup"><span data-stu-id="c0d29-172">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="c0d29-173">**OneDrive для бизнеса**</span><span class="sxs-lookup"><span data-stu-id="c0d29-173">**OneDrive for Business**</span></span>

<span data-ttu-id="c0d29-174">В средстве запуска приложений Microsoft 365 выберите OneDrive и убедитесь, что вы автоматически направляетесь к соответствующему географическому расположению пользователя с учетом PDL пользователя.</span><span class="sxs-lookup"><span data-stu-id="c0d29-174">Select OneDrive from the Microsoft 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="c0d29-175">Теперь должна начаться подготовка OneDrive для бизнеса в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="c0d29-175">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="c0d29-176">Когда подготовка будет завершена, попробуйте отправить и скачать несколько документов.</span><span class="sxs-lookup"><span data-stu-id="c0d29-176">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="c0d29-177">**Мобильное приложение OneDrive**</span><span class="sxs-lookup"><span data-stu-id="c0d29-177">**OneDrive Mobile App**</span></span>

<span data-ttu-id="c0d29-178">Войдите в мобильное приложение OneDrive, используя учетные данные тестовой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="c0d29-178">Log into your OneDrive mobile App with your test account credentials.</span></span> <span data-ttu-id="c0d29-179">Убедитесь, что файлы в OneDrive для бизнеса отображаются и вы можете работать с ними на мобильном устройстве.</span><span class="sxs-lookup"><span data-stu-id="c0d29-179">Confirm that you can see your OneDrive for Business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="c0d29-180">**Клиент синхронизации OneDrive**</span><span class="sxs-lookup"><span data-stu-id="c0d29-180">**OneDrive sync client**</span></span>

<span data-ttu-id="c0d29-181">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login.</span><span class="sxs-lookup"><span data-stu-id="c0d29-181">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login.</span></span> <span data-ttu-id="c0d29-182">If you need to download the sync client, you can click **Sync** in the OneDrive library.</span><span class="sxs-lookup"><span data-stu-id="c0d29-182">If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="c0d29-183">**Приложения Office**</span><span class="sxs-lookup"><span data-stu-id="c0d29-183">**Office applications**</span></span>

<span data-ttu-id="c0d29-184">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word.</span><span class="sxs-lookup"><span data-stu-id="c0d29-184">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word.</span></span> <span data-ttu-id="c0d29-185">Open the Office application and select "OneDrive – <TenantName>".</span><span class="sxs-lookup"><span data-stu-id="c0d29-185">Open the Office application and select "OneDrive – <TenantName>".</span></span> <span data-ttu-id="c0d29-186">Office will detect your OneDrive location and show you the files that you can open.</span><span class="sxs-lookup"><span data-stu-id="c0d29-186">Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="c0d29-187">**Общий доступ**</span><span class="sxs-lookup"><span data-stu-id="c0d29-187">**Sharing**</span></span>

<span data-ttu-id="c0d29-188">Try sharing OneDrive files.</span><span class="sxs-lookup"><span data-stu-id="c0d29-188">Try sharing OneDrive files.</span></span> <span data-ttu-id="c0d29-189">Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span><span class="sxs-lookup"><span data-stu-id="c0d29-189">Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
