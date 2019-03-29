---
title: Перемещение сайта SharePoint в другой геообъект (предварительная версия)
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Сведения о перемещении сайта SharePoint в другой геообъект.
ms.openlocfilehash: dc34b0a40789d6bf60878c050dcc654589fe940c
ms.sourcegitcommit: 37a13cafdf1695333e482f82181a04932980a6fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2019
ms.locfileid: "30936819"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location-preview"></a><span data-ttu-id="9e9e9-103">Перемещение сайта SharePoint в другой геообъект (предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="9e9e9-103">Move a SharePoint site to a different geo location (Preview)</span></span>

<span data-ttu-id="9e9e9-104">С помощью функции перемещения географического расположения сайта SharePoint можно перемещать сайты SharePoint в другие геообъекты в среде с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span> <span data-ttu-id="9e9e9-105">В настоящее время эта функция находится на стадии бета-тестирования.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-105">This feature is currently in preview.</span></span>

<span data-ttu-id="9e9e9-106">Следующие типы сайтов можно перемещать между геообъектами:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-106">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="9e9e9-107">Сайты, подключенные к группе Office 365</span><span class="sxs-lookup"><span data-stu-id="9e9e9-107">Office 365 admin sites</span></span>
- <span data-ttu-id="9e9e9-108">Современные сайты без связи с группой Office 365</span><span class="sxs-lookup"><span data-stu-id="9e9e9-108">Modern sites without an Office 365 Group association</span></span>
- <span data-ttu-id="9e9e9-109">Классические сайты SharePoint</span><span class="sxs-lookup"><span data-stu-id="9e9e9-109">Classic SharePoint sites</span></span>
- <span data-ttu-id="9e9e9-110">Информационные сайты</span><span class="sxs-lookup"><span data-stu-id="9e9e9-110">Communication sites</span></span>

<span data-ttu-id="9e9e9-111">Чтобы переместить сайт между геообъектами, необходимо быть глобальным администратором или администратором SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-111">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="9e9e9-112">Во время перемещения географического расположения сайта SharePoint возникает промежуток с доступом только для чтения продолжительностью около 4–6 часов в зависимости от содержимого сайта.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-112">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="9e9e9-113">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="9e9e9-113">Best practices</span></span>

- <span data-ttu-id="9e9e9-114">Попробуйте выполнить перемещение сайта SharePoint на тестовом сайте, чтобы познакомиться с процедурой.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-114">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="9e9e9-115">Подтвердите возможность перемещения сайта до планирования или выполнения перемещения.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-115">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="9e9e9-116">По возможности планируйте перемещение сайтов между геообъектами в нерабочие часы для уменьшения влияния на пользователей.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-116">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="9e9e9-117">Перед перемещением сайта оповестите затрагиваемых пользователей.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-117">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="9e9e9-118">Общение с пользователями</span><span class="sxs-lookup"><span data-stu-id="9e9e9-118">Communicating to your users</span></span>

<span data-ttu-id="9e9e9-119">При перемещении сайтов SharePoint из одного географического расположения в другое важно объяснить пользователям, чего ожидать.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-119">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="9e9e9-120">Это поможет избежать недоразумений и снизит количество обращений в службу поддержки.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-120">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="9e9e9-121">Перед тем как начать перемещение, отправьте пользователям по электронной почте следующую информацию:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-121">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="9e9e9-122">время начала перемещения и его длительность;</span><span class="sxs-lookup"><span data-stu-id="9e9e9-122">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="9e9e9-123">географическое расположение, в которое переносится сайт, и новый URL-адрес для доступа к нему;</span><span class="sxs-lookup"><span data-stu-id="9e9e9-123">What geo location their OneDrive is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="9e9e9-124">напомните, что необходимо закрыть файлы и не редактировать их во время перемещения;</span><span class="sxs-lookup"><span data-stu-id="9e9e9-124">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="9e9e9-125">после перемещения разрешения для файлов и параметры общего доступа к файлам остаются без изменений;</span><span class="sxs-lookup"><span data-stu-id="9e9e9-125">File permissions and sharing will not change as a result of the move.</span></span>
- <span data-ttu-id="9e9e9-126">чего ожидать от пользовательского интерфейса в среде с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-126">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="9e9e9-127">Обязательно известите пользователей сайтов об успешном окончании перемещения и сообщите, что они могут возобновить работу на сайтах.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-127">Be sure to send your users an email when the move has successfully completed informing them that they can resume working in OneDrive.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="9e9e9-128">Планирование перемещений сайтов SharePoint</span><span class="sxs-lookup"><span data-stu-id="9e9e9-128">Scheduling OneDrive site moves</span></span>

<span data-ttu-id="9e9e9-129">Вы можете заранее спланировать перемещения сайтов SharePoint (описано далее в этой статье).</span><span class="sxs-lookup"><span data-stu-id="9e9e9-129">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="9e9e9-130">Вы можете запланировать перемещения следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-130">You can schedule moves as follows:</span></span>

- <span data-ttu-id="9e9e9-131">Можно запланировать до 4000 перемещений за один раз.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-131">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="9e9e9-132">После начала перемещения можно продолжить планирование, не превышая 4000 ожидаемых перемещений в очереди в любой момент времени.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-132">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="9e9e9-133">Чтобы запланировать перемещение географического расположения сайта SharePoint на более позднее время, укажите один из следующих параметров в начале перемещения:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-133">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="9e9e9-134">`PreferredMoveBeginDate` — предполагаемое время начала перемещения.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-134">`PreferredMoveBeginDate` – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>
- <span data-ttu-id="9e9e9-135">`PreferredMoveEndDate` — предполагаемое время завершения перемещения (самый короткий период).</span><span class="sxs-lookup"><span data-stu-id="9e9e9-135">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

<span data-ttu-id="9e9e9-136">Для обоих параметров время необходимо указывать в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-136">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="9e9e9-137">Перемещение сайта</span><span class="sxs-lookup"><span data-stu-id="9e9e9-137">Moving the site</span></span>

<span data-ttu-id="9e9e9-138">Перемещение географического расположения сайта SharePoint требует подключения и выполнения перемещения из URL-адреса администрирования SharePoint в географическом расположении, в котором находится сайт.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-138">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="9e9e9-139">Например, если URL-адрес сайта — https://contosohealthcare.sharepoint.com/sites/Turbines, подключитесь к URL-адресу администрирования SharePoint https://contosohealthcare-admin.sharepoint.com:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-139">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`connect-sposervice -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="9e9e9-140">Проверка среды</span><span class="sxs-lookup"><span data-stu-id="9e9e9-140">Validating the environment</span></span>

<span data-ttu-id="9e9e9-141">Перед планированием перемещения любого сайта рекомендуется выполнить проверку, позволяющую убедиться, что сайт можно перемещать.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-141">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="9e9e9-142">Не поддерживается перемещение сайтов со следующими элементами:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-142">We do not support moving sites with:</span></span>
-   <span data-ttu-id="9e9e9-143">Службы Business Connectivity Services</span><span class="sxs-lookup"><span data-stu-id="9e9e9-143">Business Connectivity Services</span></span>
-   <span data-ttu-id="9e9e9-144">Формы InfoPath</span><span class="sxs-lookup"><span data-stu-id="9e9e9-144">InfoPath forms</span></span> 

<span data-ttu-id="9e9e9-145">Чтобы проверить, все ли геообъекты совместимы, выполните команду `Get-SPOGeoMoveCrossCompatibilityStatus`.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-145">To ensure that all geo locations are compatible, run:</span></span> <span data-ttu-id="9e9e9-146">Она отобразит все ваши геообъекты и укажет, совместима ли среда с целевым географическим расположением.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-146">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="9e9e9-147">Чтобы выполнить на сайте только проверочную операцию, используйте `Start-SPOSiteContentMove` с параметром `-ValidationOnly` для проверки возможности перемещения сайта.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-147">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="9e9e9-148">Пример:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-148">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="9e9e9-149">В результате будет возвращено значение *Success*, если сайт готов к перемещению или *Fail*, если имеются какие-либо препятствия.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-149">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a><span data-ttu-id="9e9e9-150">Запуск перемещения географического расположения сайта SharePoint для сайта, не связанного с группой Office 365</span><span class="sxs-lookup"><span data-stu-id="9e9e9-150">Start a SharePoint site geo move for a site with no associated Office 365 Group</span></span>

<span data-ttu-id="9e9e9-151">По умолчанию исходный URL-адрес для сайта изменяется на URL-адрес целевого географического расположения.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-151">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="9e9e9-152">Пример:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-152">For example:</span></span>

<span data-ttu-id="9e9e9-153">https://Contoso.sharepoint.com/sites/projectx меняется на https://Contoso.sharepointEUR.com/sites/projectx</span><span class="sxs-lookup"><span data-stu-id="9e9e9-153">https://Contoso.sharepoint.com/sites/projectxtohttps://Contoso.sharepointEUR.com/sites/projectx</span></span>

<span data-ttu-id="9e9e9-154">Сайты, не связанные с группой Office 365, также можно переименовать с помощью параметра `-DestinationUrl`.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-154">For sites with no Office 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="9e9e9-155">Пример:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-155">For example:</span></span>

<span data-ttu-id="9e9e9-156">https://Contoso.sharepoint.com/sites/projectx меняется на https://Contoso.sharepointEUR.com/sites/projecty</span><span class="sxs-lookup"><span data-stu-id="9e9e9-156">https://Contoso.sharepoint.com/sites/projectxtohttps://Contoso.sharepointEUR.com/sites/projecty</span></span>

<span data-ttu-id="9e9e9-157">Чтобы начать перемещение сайта, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-157">To start the move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Снимок экрана: окно PowerShell с командлетом Start-SPOSiteContentMove](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a><span data-ttu-id="9e9e9-159">Запуск перемещения географического расположения сайта SharePoint для сайта, подключенного к группе Office 365</span><span class="sxs-lookup"><span data-stu-id="9e9e9-159">Start a SharePoint site geo move for an Office 365 Group-connected site</span></span>

<span data-ttu-id="9e9e9-160">Чтобы переместить сайт, подключенный к группе Office 365, глобальный администратор должен сначала изменить атрибут предпочтительного расположения данных (PDL) для группы Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-160">To move an Office 365 Group-connected site, the global administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="9e9e9-161">Настройка атрибута PDL для группы Office 365:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-161">To set the PDL for an Office 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="9e9e9-162">После обновления атрибута PDL вы можете начать перемещение сайта:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-162">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="9e9e9-163">Отмена перемещения географического расположения сайта SharePoint</span><span class="sxs-lookup"><span data-stu-id="9e9e9-163">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="9e9e9-164">Перемещение географического расположения сайта SharePoint можно остановить, если этот процесс не находится на этапе выполнения или не завершен с помощью командлета `Stop-SPOSiteContentMove`.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-164">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="9e9e9-165">Определение состояния перемещения географического расположения сайта SharePoint</span><span class="sxs-lookup"><span data-stu-id="9e9e9-165">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="9e9e9-166">Вы можете определить состояние перемещения сайта в отношении геообъекта (в расположение или из расположения), к которому подключены, с помощью следующих командлетов:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-166">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="9e9e9-167">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (сайты, не подключенные к группе)</span><span class="sxs-lookup"><span data-stu-id="9e9e9-167">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="9e9e9-168">Get-SPOUnifiedGroupMoveState (сайты, подключенные к группе)</span><span class="sxs-lookup"><span data-stu-id="9e9e9-168">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="9e9e9-169">Используйте параметр `-SourceSiteUrl`, чтобы указать сайт, для которого нужно просмотреть состояние перемещения.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-169">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="9e9e9-170">Состояния перемещения описаны в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-170">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="9e9e9-171">Состояние</span><span class="sxs-lookup"><span data-stu-id="9e9e9-171">Status</span></span>|<span data-ttu-id="9e9e9-172">Описание</span><span class="sxs-lookup"><span data-stu-id="9e9e9-172">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="9e9e9-173">Ready to Trigger</span><span class="sxs-lookup"><span data-stu-id="9e9e9-173">Ready to Trigger</span></span>|<span data-ttu-id="9e9e9-174">Перемещение не начато.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-174">The move has not started.</span></span>|
|<span data-ttu-id="9e9e9-175">Scheduled</span><span class="sxs-lookup"><span data-stu-id="9e9e9-175">Scheduled Unpublish</span></span>|<span data-ttu-id="9e9e9-176">Перемещение в очереди, но еще не началось.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-176">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="9e9e9-177">InProgress (n/4)</span><span class="sxs-lookup"><span data-stu-id="9e9e9-177">InProgress (n/4)</span></span>|<span data-ttu-id="9e9e9-178">Перемещение в процессе и находится в одном из следующих состояний: "проверка" (1/4), "резервное копирование" (2/4), "восстановление" (3/4), "очистка" (4/4).</span><span class="sxs-lookup"><span data-stu-id="9e9e9-178">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="9e9e9-179">Success</span><span class="sxs-lookup"><span data-stu-id="9e9e9-179">Success</span></span>|<span data-ttu-id="9e9e9-180">Перемещение успешно завершено.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-180">The move has completed successfully.</span></span>|
|<span data-ttu-id="9e9e9-181">Failed</span><span class="sxs-lookup"><span data-stu-id="9e9e9-181">Failed</span></span>|<span data-ttu-id="9e9e9-182">Перемещение не удалось выполнить.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-182">The move failed.</span></span>|

<span data-ttu-id="9e9e9-183">Вы также можете применить параметр `-Verbose`, чтобы просмотреть дополнительные сведения о перемещении.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-183">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="9e9e9-184">Взаимодействие с пользователем</span><span class="sxs-lookup"><span data-stu-id="9e9e9-184">User experience</span></span>

<span data-ttu-id="9e9e9-185">Перемещение сайта в другой геообъект должно проходить максимально незаметно для пользователей сайта.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-185">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="9e9e9-186">Если не считать кратковременного состояния доступа только для чтения при перемещении, после завершения этого процесса существующие ссылки и разрешения будут доступны в обычном режиме.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-186">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="9e9e9-187">Сайт</span><span class="sxs-lookup"><span data-stu-id="9e9e9-187">Site</span></span>

<span data-ttu-id="9e9e9-188">Во время перемещения сайт доступен только для чтения.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-188">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="9e9e9-189">Когда перемещение завершится, при попытке пользователя щелкнуть закладку или другую ссылку, ведущую к сайту, он будет направлен к новому сайту в новом географическом расположении.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-189">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="9e9e9-190">Разрешения</span><span class="sxs-lookup"><span data-stu-id="9e9e9-190">Permissions</span></span>

<span data-ttu-id="9e9e9-191">У пользователей с разрешениями для сайта будет к нему доступ во время перемещения и после его завершения.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-191">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="9e9e9-192">Клиент синхронизации</span><span class="sxs-lookup"><span data-stu-id="9e9e9-192">Sync Client</span></span>

<span data-ttu-id="9e9e9-193">Когда будет выполнено перемещение сайта, клиент синхронизации автоматически обнаружит и легко перенесет синхронизацию в новое расположение сайта.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-193">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="9e9e9-194">Пользователю не нужно выполнять повторный вход или любые другие действия.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-194">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="9e9e9-195">(Требуется клиент синхронизации версии 17.3.6943.0625 или более поздней.)</span><span class="sxs-lookup"><span data-stu-id="9e9e9-195">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="9e9e9-196">Если пользователь попробует обновить файл во время перемещения, клиент синхронизации уведомит его о том, что отправка файла при выполнении перемещения приостанавливается.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-196">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="9e9e9-197">Предоставление ссылок</span><span class="sxs-lookup"><span data-stu-id="9e9e9-197">Sharing links</span></span>

<span data-ttu-id="9e9e9-198">Когда перемещение географического расположения сайта SharePoint будет завершено, для существующих предоставленных ссылок на перемещенные файлы будет автоматически выполняться перенаправление на новый геообъект.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-198">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="9e9e9-199">Недавно использованные файлы в Office (MRU)</span><span class="sxs-lookup"><span data-stu-id="9e9e9-199">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="9e9e9-200">Служба MRU обновляется с URL-адресом сайта и URL-адресами его содержимого после завершения перемещения.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-200">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="9e9e9-201">Это применяется к Word, Excel и PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-201">This currently applies to Word, Excel, and PowerPoint add-ins that are free in AppSource.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="9e9e9-202">Интерфейс OneNote</span><span class="sxs-lookup"><span data-stu-id="9e9e9-202">OneNote Experience</span></span>

<span data-ttu-id="9e9e9-203">Когда перемещение сайта будет завершено, приложение UWP (универсальное) и клиент OneNote win32 автоматически обнаружат и легко синхронизируют записные книжки с новым расположением сайта.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-203">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="9e9e9-204">Пользователю не нужно выполнять повторный вход или любые другие действия.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-204">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="9e9e9-205">Во время выполнения перемещения сайта единственным отображаемым индикатором для пользователя является уведомление об ошибке синхронизации записной книжки.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-205">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="9e9e9-206">Эта возможность доступна для следующих клиентских версий OneNote:</span><span class="sxs-lookup"><span data-stu-id="9e9e9-206">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="9e9e9-207">OneNote win32 версии 16.0.8326.2096 (или более поздней);</span><span class="sxs-lookup"><span data-stu-id="9e9e9-207">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="9e9e9-208">OneNote UWP версии 16.0.8431.1006 (или более поздней);</span><span class="sxs-lookup"><span data-stu-id="9e9e9-208">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="9e9e9-209">приложение OneNote Mobile версии 16.0.8431.1011 (или более поздней).</span><span class="sxs-lookup"><span data-stu-id="9e9e9-209">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-office-365-group-connected-sites"></a><span data-ttu-id="9e9e9-210">Teams (применимо к сайтам, подключенным к группе Office 365)</span><span class="sxs-lookup"><span data-stu-id="9e9e9-210">Teams (applicable to Office 365 Group connected sites)</span></span>

<span data-ttu-id="9e9e9-211">Когда перемещение географического расположения сайта SharePoint будет завершено, пользователи получат доступ к файлам сайта, подключенного к группе Office 365, в приложении Teams.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-211">When the SharePoint site geo move completes, users will have access to their Office 365 Group site files on the Teams app.</span></span> <span data-ttu-id="9e9e9-212">Кроме того, файлы, отправленные из сайта через чат Teams до такого перемещения, будут продолжать работать и после него.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-212">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="9e9e9-213">Мобильное приложение SharePoint (iOS или Android)</span><span class="sxs-lookup"><span data-stu-id="9e9e9-213">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="9e9e9-214">Мобильное приложение SharePoint совместимо с переносом географических расположений и может определять новое географическое расположение сайта.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-214">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="9e9e9-215">Рабочие процессы SharePoint</span><span class="sxs-lookup"><span data-stu-id="9e9e9-215">SharePoint workflows</span></span>

<span data-ttu-id="9e9e9-216">Рабочие процессы SharePoint 2013 требуют повторной публикации после перемещения сайта.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-216">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="9e9e9-217">Рабочие процессы SharePoint 2010 должны продолжать нормально работать.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-217">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="9e9e9-218">Приложения</span><span class="sxs-lookup"><span data-stu-id="9e9e9-218">Apps</span></span>

<span data-ttu-id="9e9e9-219">Если вы перемещаете сайт с приложениями, необходимо повторно создать экземпляр приложения в новом географическом расположении сайта, так как приложение и его связи могут быть недоступны в конечном геообъекте.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-219">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="9e9e9-220">Flow</span><span class="sxs-lookup"><span data-stu-id="9e9e9-220">Flow</span></span>

<span data-ttu-id="9e9e9-221">В большинстве случаев потоки Flow будут продолжать работать после перемещения географического расположения сайта SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-221">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="9e9e9-222">Рекомендуется проверить их после завершения перемещения.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-222">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="9e9e9-223">PowerApps</span><span class="sxs-lookup"><span data-stu-id="9e9e9-223">PowerApps</span></span>

<span data-ttu-id="9e9e9-224">Для PowerApps требуется повторное создание в конечном расположении.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-224">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="9e9e9-225">Перемещение данных между географическими расположениями</span><span class="sxs-lookup"><span data-stu-id="9e9e9-225">Data movement between geo locations</span></span>

<span data-ttu-id="9e9e9-226">SharePoint использует хранилище BLOB-объектов Azure для своего содержимого, а метаданные, связанные с сайтами и файлами, хранятся в SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-226">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="9e9e9-227">После перемещения сайта из исходного в новое географическое расположение служба также переместит связанное хранилище BLOB-объектов.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-227">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="9e9e9-228">Перемещение хранилища BLOB-объектов завершается примерно за 40 дней.</span><span class="sxs-lookup"><span data-stu-id="9e9e9-228">Blob Storage moves complete in approximately 40 days.</span></span> 
