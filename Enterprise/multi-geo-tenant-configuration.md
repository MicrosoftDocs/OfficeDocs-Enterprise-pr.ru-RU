---
title: Конфигурация клиента Office 365 с поддержкой нескольких регионов
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Сведения о настройке Office 365 с поддержкой нескольких регионов
ms.openlocfilehash: 6a3282c65da79480fe9d7ed1aac24b5e7941c1fc
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487572"
---
# <a name="office-365-multi-geo-tenant-configuration"></a><span data-ttu-id="398fd-103">Конфигурация клиента Office 365 с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="398fd-103">Office 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="398fd-104">Прежде чем настраивать клиент Office 365 с поддержкой нескольких регионов, прочтите статью [Планирование использования Office 365 с поддержкой нескольких регионов](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="398fd-104">Before you configure your tenant for Office 365 Multi-Geo, be sure you have read [Plan for Office 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="398fd-105">Чтобы выполнить шаги, описанные в этой статье, вам понадобится список географических расположений, которые нужно включить в качестве периферийных расположений, а также тестовые пользователи, которых нужно подготовить к работе для этих расположений.</span><span class="sxs-lookup"><span data-stu-id="398fd-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="398fd-106">Добавление поддержки нескольких регионов в план Office 365 для клиента</span><span class="sxs-lookup"><span data-stu-id="398fd-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="398fd-107">Чтобы можно было использовать Office 365 с поддержкой нескольких регионов, вам понадобится _план поддержки нескольких регионов в Office 365_.</span><span class="sxs-lookup"><span data-stu-id="398fd-107">To use Office 365 Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan.</span></span> <span data-ttu-id="398fd-108">Вместе с сотрудниками, занимающимися учетными записями, добавьте этот план для клиента.</span><span class="sxs-lookup"><span data-stu-id="398fd-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="398fd-109">Эти сотрудники свяжут вас с подходящим специалистом по лицензированию и помогут настроить клиент.</span><span class="sxs-lookup"><span data-stu-id="398fd-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="398fd-p103">Обратите внимание, что _план поддержки нескольких регионов в Office 365_ — это план обслуживания на уровне пользователя. Для каждого пользователя, которого нужно разместить в периферийном геообъекте, понадобится лицензия. Постепенно можно добавлять дополнительные лицензии по мере добавления пользователей в периферийные географические расположения.</span><span class="sxs-lookup"><span data-stu-id="398fd-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="398fd-113">Когда клиент будет подготовлен к работе с использованием _плана поддержки нескольких регионов в Office 365_, в Центрах администрирования OneDrive и SharePoint станет доступной вкладка **Географические расположения**.</span><span class="sxs-lookup"><span data-stu-id="398fd-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="398fd-114">Добавление периферийных расположений к клиенту</span><span class="sxs-lookup"><span data-stu-id="398fd-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="398fd-115">Для каждого географического расположения, в котором нужно хранить данные, необходимо добавить периферийное расположение.</span><span class="sxs-lookup"><span data-stu-id="398fd-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="398fd-116">Доступные географические расположения показаны в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="398fd-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Снимок экрана: страница географических расположений в Центре администрирования SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="398fd-118">Добавление периферийного расположения</span><span class="sxs-lookup"><span data-stu-id="398fd-118">To add a satellite location</span></span>

1. <span data-ttu-id="398fd-119">Откройте Центр администрирования SharePoint.</span><span class="sxs-lookup"><span data-stu-id="398fd-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="398fd-120">Перейдите на вкладку **Географические расположения**.</span><span class="sxs-lookup"><span data-stu-id="398fd-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="398fd-121">Нажмите кнопку **Добавить расположение**.</span><span class="sxs-lookup"><span data-stu-id="398fd-121">Click **Add location**.</span></span>

4. <span data-ttu-id="398fd-122">Выберите нужное расположение и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="398fd-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="398fd-123">Укажите домен, который хотите использовать для географического расположения, и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="398fd-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="398fd-124">Нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="398fd-124">Click **Close**.</span></span>

<span data-ttu-id="398fd-p105">В зависимости от размера клиента подготовка к работе может занять от нескольких до 72 часов. Как только подготовка вспомогательного расположения завершится, вы получите подтверждение по электронной почте. Когда новое географическое расположение отобразится в синем цвете на карте вкладки **Географические расположения** в Центре администрирования OneDrive, вы сможете перейти к настройке предпочтительного расположения данных пользователей для этого географического расположения.</span><span class="sxs-lookup"><span data-stu-id="398fd-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="398fd-p106">Для нового периферийного расположения будут заданы параметры по умолчанию. Это позволит настроить его в соответствии с локальными требованиями.</span><span class="sxs-lookup"><span data-stu-id="398fd-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="398fd-130">Настройка предпочтительного расположения данных пользователей</span><span class="sxs-lookup"><span data-stu-id="398fd-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="398fd-p107">Настроив необходимые периферийные расположения данных, вы можете обновить учетные записи пользователей для применения соответствующих предпочтительных расположений данных. Рекомендуем задать предпочтительное расположение данных для каждого пользователя, даже если какие-то пользователи остаются в центральном расположении.</span><span class="sxs-lookup"><span data-stu-id="398fd-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="398fd-133">Если для предпочтительного расположения данных пользователя задано расположение, не настроенное в качестве периферийного или центрального, система по умолчанию использует центральное расположение при подготовке сайтов OneDrive и SharePoint, а также почтовых ящиков групп.</span><span class="sxs-lookup"><span data-stu-id="398fd-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="398fd-134">Прежде чем развертывать поддержку нескольких регионов для всей организации, рекомендуем начать проверки с вовлечением тестового пользователя или небольшой группы пользователей.</span><span class="sxs-lookup"><span data-stu-id="398fd-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="398fd-135">В Azure Active Directory существует два типа объектов пользователя: синхронизированные и только облачные.</span><span class="sxs-lookup"><span data-stu-id="398fd-135">In Azure Active Directory there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="398fd-136">Следуйте соответствующим инструкциям для вашего типа пользователей.</span><span class="sxs-lookup"><span data-stu-id="398fd-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a><span data-ttu-id="398fd-137">Синхронизация предпочтительного расположения данных пользователя с помощью Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="398fd-137">Synchronize user's Preferred Data Location using Azure Active Directory Connect</span></span> 

<span data-ttu-id="398fd-p109">Если пользователи вашей организации синхронизируются из системы локальной службы Active Directory в Azure Active Directory, соответствующий параметр PreferredDataLocation должен быть заполнен в AD и синхронизирован с AAD. Чтобы настроить синхронизацию предпочтительных расположений данных из локальной службы Active Directory в Azure Active Directory, следуйте инструкциям из [этой статьи](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="398fd-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="398fd-140">Рекомендуем включить настройку предпочтительного расположения данных пользователя в стандартный рабочий процесс создания пользователей.</span><span class="sxs-lookup"><span data-stu-id="398fd-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="398fd-141">В случае новых пользователей, для которых служба OneDrive не подготовлена к работе, следует подождать по крайней мере 24 часа после синхронизации PDL в Azure Active Directory пользователя. Это срок распространения изменений, по завершении которого пользователи смогут войти в OneDrive для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="398fd-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="398fd-142">(Настройка предпочтительного расположения данных до входа пользователя с целью подготовки к работе OneDrive для бизнеса позволяет обеспечить подготовку OneDrive в правильном расположении.)</span><span class="sxs-lookup"><span data-stu-id="398fd-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="398fd-143">Настройка предпочтительного расположения данных для облачных пользователей</span><span class="sxs-lookup"><span data-stu-id="398fd-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="398fd-144">Если пользователи вашей организации не синхронизируются из системы локальной службы Active Directory в Azure Active Directory, то есть создаются в Office 365 или Azure Active Directory, задать PDL нужно с помощью Azure Active Directory PowerShell.</span><span class="sxs-lookup"><span data-stu-id="398fd-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Office 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="398fd-p111">Процедуры, описанные в этом разделе, требуют наличия [модуля Microsoft Azure Active Directory для Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Если вы уже установили Azure Active Directory PowerShell, нужно обновление до последней версии.</span><span class="sxs-lookup"><span data-stu-id="398fd-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="398fd-147">Откройте модуль Microsoft Azure Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="398fd-147">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="398fd-148">Запустите командлет `Connect-MsolService` и введите учетные данные глобального администратора для своего клиента.</span><span class="sxs-lookup"><span data-stu-id="398fd-148">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="398fd-p112">Запустите командлет [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser), чтобы задать предпочтительное расположение данных для каждого из пользователей. Пример:</span><span class="sxs-lookup"><span data-stu-id="398fd-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="398fd-p113">Командлет Get-MsolUser позволяет проверить обновление предпочтительного расположения данных. Пример:</span><span class="sxs-lookup"><span data-stu-id="398fd-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Снимок экрана: окно PowerShell с командлетом set-msoluser](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="398fd-154">Рекомендуем включить настройку предпочтительного расположения данных пользователя в стандартный рабочий процесс создания пользователей.</span><span class="sxs-lookup"><span data-stu-id="398fd-154">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="398fd-155">В случае новых пользователей, для которых служба OneDrive не подготовлена к работе, следует подождать по крайней мере 24 часа после настройки PDL пользователя. Это срок распространения изменений, по завершении которого пользователи смогут войти в OneDrive.</span><span class="sxs-lookup"><span data-stu-id="398fd-155">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="398fd-156">(Настройка предпочтительного расположения данных до входа пользователя с целью подготовки к работе OneDrive для бизнеса позволяет обеспечить подготовку OneDrive в правильном расположении.)</span><span class="sxs-lookup"><span data-stu-id="398fd-156">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="398fd-157">Подготовка к работе OneDrive и влияние PDL</span><span class="sxs-lookup"><span data-stu-id="398fd-157">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="398fd-158">Если у пользователя уже есть сайт OneDrive, созданный в клиенте, при настройке его PDL не будет автоматически выполняться перемещение его сайта OneDrive.</span><span class="sxs-lookup"><span data-stu-id="398fd-158">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="398fd-159">Чтобы переместить сайт OneDrive пользователя, см. статью [Перемещение OneDrive для бизнеса в отношении геообъекта](move-onedrive-between-geo-locations.md). Выполните инструкции из раздела о перемещении OneDrive из одного геообъекта в другой.</span><span class="sxs-lookup"><span data-stu-id="398fd-159">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="398fd-160">(Обратите внимание, что почтовый ящик Exchange пользователя не перемещается автоматически при настройке PDL пользователя.)</span><span class="sxs-lookup"><span data-stu-id="398fd-160">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="398fd-161">Если у пользователя нет сайта OneDrive в клиенте, для этого пользователя будет выполнена подготовка OneDrive к работе в соответствии со значением его PDL (при условии, что PDL пользователя соответствует одному из периферийных расположений компании).</span><span class="sxs-lookup"><span data-stu-id="398fd-161">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="398fd-162">Настройка поиска с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="398fd-162">Configuring Multi-Geo search</span></span>

<span data-ttu-id="398fd-163">Для клиента с несколькими регионами будет доступен поиск с объединением результатов, благодаря которому при отправке поискового запроса будут возвращаться данные из любого расположения клиента.</span><span class="sxs-lookup"><span data-stu-id="398fd-163">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="398fd-164">По умолчанию возвращаются объединенные результаты, даже когда каждый индекс поиска находится в пределах релевантного геообъекта, если поиск выполняется из этих точек входа:</span><span class="sxs-lookup"><span data-stu-id="398fd-164">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="398fd-165">OneDrive для бизнеса;</span><span class="sxs-lookup"><span data-stu-id="398fd-165">OneDrive for business</span></span>

- <span data-ttu-id="398fd-166">Delve;</span><span class="sxs-lookup"><span data-stu-id="398fd-166">Delve</span></span>

- <span data-ttu-id="398fd-167">домашняя страница SharePoint;</span><span class="sxs-lookup"><span data-stu-id="398fd-167">SharePoint Home</span></span>

- <span data-ttu-id="398fd-168">центр поиска.</span><span class="sxs-lookup"><span data-stu-id="398fd-168">Search Center</span></span>

<span data-ttu-id="398fd-169">Кроме этого, возможности поиска с поддержкой нескольких регионов можно настроить для специальных поисковых приложений, которые используют API поиска SharePoint.</span><span class="sxs-lookup"><span data-stu-id="398fd-169">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="398fd-170">Ознакомьтесь со статьей [Настройка поиска в OneDrive для бизнеса с поддержкой нескольких регионов](configure-search-for-multi-geo.md), в которой изложены соответствующие инструкции, а также описаны ограничения и различия.</span><span class="sxs-lookup"><span data-stu-id="398fd-170">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-office-365-multi-geo-configuration"></a><span data-ttu-id="398fd-171">Проверка конфигурации Office 365 с поддержкой нескольких регионов</span><span class="sxs-lookup"><span data-stu-id="398fd-171">Validating the Office 365 Multi-Geo configuration</span></span>

<span data-ttu-id="398fd-172">Ниже приведены некоторые основные варианты использования, которые можно включить в свой план проверки перед полным развертыванием Office 365 с поддержкой нескольких регионов в организации.</span><span class="sxs-lookup"><span data-stu-id="398fd-172">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Office 365 Multi-Geo to your company.</span></span> <span data-ttu-id="398fd-173">Выполнив эти тесты и проработав дополнительные варианты использования, подходящие для вашей организации, можно перейти к добавлению пользователей в начальную пилотную группу.</span><span class="sxs-lookup"><span data-stu-id="398fd-173">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="398fd-174">**OneDrive для бизнеса**</span><span class="sxs-lookup"><span data-stu-id="398fd-174">**OneDrive for Business**</span></span>

<span data-ttu-id="398fd-175">В средстве запуска приложений Office 365 выберите OneDrive и убедитесь, что вы автоматически направляетесь к соответствующему географическому расположению пользователя с учетом PDL пользователя.</span><span class="sxs-lookup"><span data-stu-id="398fd-175">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="398fd-176">Теперь должна начаться подготовка OneDrive для бизнеса в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="398fd-176">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="398fd-177">Когда подготовка будет завершена, попробуйте отправить и скачать несколько документов.</span><span class="sxs-lookup"><span data-stu-id="398fd-177">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="398fd-178">**Мобильное приложение OneDrive**</span><span class="sxs-lookup"><span data-stu-id="398fd-178">**OneDrive Mobile App**</span></span>

<span data-ttu-id="398fd-p118">Войдите в мобильное приложение OneDrive, используя тестовые учетные данные. Убедитесь, что файлы в OneDrive для бизнеса отображаются и вы можете с ними работать на мобильном устройстве.</span><span class="sxs-lookup"><span data-stu-id="398fd-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="398fd-181">**Клиент синхронизации OneDrive**</span><span class="sxs-lookup"><span data-stu-id="398fd-181">**OneDrive sync client**</span></span>

<span data-ttu-id="398fd-p119">Убедитесь в том, что клиент синхронизации OneDrive автоматически определяет географическое расположение OneDrive для бизнеса после входа. Если вам нужно скачать клиент синхронизации, в библиотеке OneDrive выберите **Синхронизация**.</span><span class="sxs-lookup"><span data-stu-id="398fd-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="398fd-184">**Приложения Office**</span><span class="sxs-lookup"><span data-stu-id="398fd-184">**Office applications**</span></span>

<span data-ttu-id="398fd-p120">Убедитесь, что можете войти в OneDrive для бизнеса из приложения Office, например Word. Откройте приложение Office и выберите "OneDrive – <TenantName>". Office обнаружит географическое расположение OneDrive и отобразит файлы, которые вы можете открыть.</span><span class="sxs-lookup"><span data-stu-id="398fd-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="398fd-188">**Общий доступ**</span><span class="sxs-lookup"><span data-stu-id="398fd-188">**Sharing**</span></span>

<span data-ttu-id="398fd-p121">Попробуйте предоставить доступ к файлам в OneDrive. Убедитесь в том, что средство выбора людей показывает вам всех пользователей SharePoint Online независимо от того, каковы их географические расположения.</span><span class="sxs-lookup"><span data-stu-id="398fd-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
