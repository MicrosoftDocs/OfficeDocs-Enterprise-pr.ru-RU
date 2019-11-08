---
title: Перемещение сайта SharePoint в другой геообъект
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Сведения о перемещении сайта SharePoint в другой геообъект.
ms.openlocfilehash: 3ba95215860646691e511b17d509dbbc49a5a75a
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033445"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a><span data-ttu-id="b4eb2-103">Перемещение сайта SharePoint в другой геообъект</span><span class="sxs-lookup"><span data-stu-id="b4eb2-103">Move a SharePoint site to a different geo location</span></span>

<span data-ttu-id="b4eb2-104">С помощью функции перемещения географического расположения сайта SharePoint можно перемещать сайты SharePoint в другие геообъекты в среде с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span>

<span data-ttu-id="b4eb2-105">Следующие типы сайтов можно перемещать между геообъектами:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-105">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="b4eb2-106">Сайты, подключенные к группе Office 365</span><span class="sxs-lookup"><span data-stu-id="b4eb2-106">Office 365 Group-connected sites</span></span>
- <span data-ttu-id="b4eb2-107">Современные сайты без связи с группой Office 365</span><span class="sxs-lookup"><span data-stu-id="b4eb2-107">Modern sites without an Office 365 Group association</span></span>
- <span data-ttu-id="b4eb2-108">Классические сайты SharePoint</span><span class="sxs-lookup"><span data-stu-id="b4eb2-108">Classic SharePoint sites</span></span>
- <span data-ttu-id="b4eb2-109">Информационные сайты</span><span class="sxs-lookup"><span data-stu-id="b4eb2-109">Communication sites</span></span>

<span data-ttu-id="b4eb2-110">Чтобы переместить сайт между геообъектами, необходимо быть глобальным администратором или администратором SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-110">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="b4eb2-111">Во время перемещения географического расположения сайта SharePoint возникает промежуток с доступом только для чтения продолжительностью около 4–6 часов в зависимости от содержимого сайта.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-111">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="b4eb2-112">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="b4eb2-112">Best practices</span></span>

- <span data-ttu-id="b4eb2-113">Попробуйте выполнить перемещение сайта SharePoint на тестовом сайте, чтобы познакомиться с процедурой.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-113">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="b4eb2-114">Подтвердите возможность перемещения сайта до планирования или выполнения перемещения.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-114">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="b4eb2-115">По возможности планируйте перемещение сайтов между геообъектами в нерабочие часы для уменьшения влияния на пользователей.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-115">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="b4eb2-116">Перед перемещением сайта оповестите затрагиваемых пользователей.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-116">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="b4eb2-117">Общение с пользователями</span><span class="sxs-lookup"><span data-stu-id="b4eb2-117">Communicating to your users</span></span>

<span data-ttu-id="b4eb2-118">При перемещении сайтов SharePoint из одного географического расположения в другое важно объяснить пользователям, чего ожидать.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-118">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="b4eb2-119">Это поможет избежать недоразумений и снизит количество обращений в службу поддержки.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-119">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="b4eb2-120">Перед тем как начать перемещение, отправьте пользователям по электронной почте следующую информацию:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-120">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="b4eb2-121">время начала перемещения и его длительность;</span><span class="sxs-lookup"><span data-stu-id="b4eb2-121">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="b4eb2-122">географическое расположение, в которое переносится сайт, и новый URL-адрес для доступа к нему;</span><span class="sxs-lookup"><span data-stu-id="b4eb2-122">What geo location their site is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="b4eb2-123">напомните, что необходимо закрыть файлы и не редактировать их во время перемещения;</span><span class="sxs-lookup"><span data-stu-id="b4eb2-123">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="b4eb2-124">после перемещения разрешения для файлов и параметры общего доступа к файлам остаются без изменений;</span><span class="sxs-lookup"><span data-stu-id="b4eb2-124">File permissions and sharing will not change because of the move.</span></span>
- <span data-ttu-id="b4eb2-125">чего ожидать от пользовательского интерфейса в среде с поддержкой нескольких регионов.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-125">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="b4eb2-126">Обязательно известите пользователей сайтов об успешном окончании перемещения и сообщите, что они могут возобновить работу на сайтах.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-126">Be sure to send your sites' users an email when the move has successfully completed informing them that they can resume working on their sites.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="b4eb2-127">Планирование перемещений сайтов SharePoint</span><span class="sxs-lookup"><span data-stu-id="b4eb2-127">Scheduling SharePoint site moves</span></span>

<span data-ttu-id="b4eb2-128">Вы можете заранее спланировать перемещения сайтов SharePoint (описано далее в этой статье).</span><span class="sxs-lookup"><span data-stu-id="b4eb2-128">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="b4eb2-129">Вы можете запланировать перемещения следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-129">You can schedule moves as follows:</span></span>

- <span data-ttu-id="b4eb2-130">Можно запланировать до 4000 перемещений за один раз.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="b4eb2-131">После начала перемещения можно продолжить планирование, не превышая 4000 ожидаемых перемещений в очереди в любой момент времени.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="b4eb2-132">Чтобы запланировать перемещение географического расположения сайта SharePoint на более позднее время, укажите один из следующих параметров в начале перемещения:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-132">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="b4eb2-133">`PreferredMoveBeginDate` — предполагаемое время начала перемещения.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-133">`PreferredMoveBeginDate` – The move will likely begin at this specified time.</span></span>
- <span data-ttu-id="b4eb2-134">`PreferredMoveEndDate` — предполагаемое время завершения перемещения (самый короткий период).</span><span class="sxs-lookup"><span data-stu-id="b4eb2-134">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis.</span></span> 

<span data-ttu-id="b4eb2-135">Для обоих параметров время необходимо указывать в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-135">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="b4eb2-136">Перемещение сайта</span><span class="sxs-lookup"><span data-stu-id="b4eb2-136">Moving the site</span></span>

<span data-ttu-id="b4eb2-137">Перемещение географического расположения сайта SharePoint требует подключения и выполнения перемещения из URL-адреса администрирования SharePoint в географическом расположении, в котором находится сайт.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-137">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="b4eb2-138">Например, если URL-адрес сайта — https://contosohealthcare.sharepoint.com/sites/Turbines, подключитесь к URL-адресу администрирования SharePoint https://contosohealthcare-admin.sharepoint.com:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-138">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`connect-sposervice -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="b4eb2-139">Проверка среды</span><span class="sxs-lookup"><span data-stu-id="b4eb2-139">Validating the environment</span></span>

<span data-ttu-id="b4eb2-140">Перед планированием перемещения любого сайта рекомендуется выполнить проверку, позволяющую убедиться, что сайт можно перемещать.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-140">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="b4eb2-141">Не поддерживается перемещение сайтов со следующими элементами:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-141">We do not support moving sites with:</span></span>
-   <span data-ttu-id="b4eb2-142">Службы Business Connectivity Services</span><span class="sxs-lookup"><span data-stu-id="b4eb2-142">Business Connectivity Services</span></span>
-   <span data-ttu-id="b4eb2-143">Формы InfoPath</span><span class="sxs-lookup"><span data-stu-id="b4eb2-143">InfoPath forms</span></span> 

<span data-ttu-id="b4eb2-144">Чтобы проверить, все ли геообъекты совместимы, выполните команду `Get-SPOGeoMoveCrossCompatibilityStatus`.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-144">To ensure all geo locations are compatible, run `Get-SPOGeoMoveCrossCompatibilityStatus`.</span></span> <span data-ttu-id="b4eb2-145">Она отобразит все ваши геообъекты и укажет, совместима ли среда с целевым географическим расположением.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-145">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="b4eb2-146">Чтобы выполнить на сайте только проверочную операцию, используйте `Start-SPOSiteContentMove` с параметром `-ValidationOnly` для проверки возможности перемещения сайта.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-146">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="b4eb2-147">Пример:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-147">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="b4eb2-148">В результате будет возвращено значение *Success*, если сайт готов к перемещению или *Fail*, если имеются какие-либо препятствия.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-148">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a><span data-ttu-id="b4eb2-149">Запуск перемещения географического расположения сайта SharePoint для сайта, не связанного с группой Office 365</span><span class="sxs-lookup"><span data-stu-id="b4eb2-149">Start a SharePoint site geo move for a site with no associated Office 365 Group</span></span>

<span data-ttu-id="b4eb2-150">По умолчанию исходный URL-адрес для сайта изменяется на URL-адрес целевого географического расположения.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-150">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="b4eb2-151">Пример:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-151">For example:</span></span>

<span data-ttu-id="b4eb2-152">https://Contoso.sharepoint.com/sites/projectx меняется на https://ContosoEUR.sharepoint.com/sites/projectx</span><span class="sxs-lookup"><span data-stu-id="b4eb2-152">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projectx</span></span>

<span data-ttu-id="b4eb2-153">Сайты, не связанные с группой Office 365, также можно переименовать с помощью параметра `-DestinationUrl`.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-153">For sites with no Office 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="b4eb2-154">Пример:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-154">For example:</span></span>

<span data-ttu-id="b4eb2-155">https://Contoso.sharepoint.com/sites/projectx меняется на https://ContosoEUR.sharepoint.com/sites/projecty</span><span class="sxs-lookup"><span data-stu-id="b4eb2-155">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projecty</span></span>

<span data-ttu-id="b4eb2-156">Чтобы начать перемещение сайта, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-156">To start the site move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Снимок экрана: окно PowerShell с командлетом Start-SPOSiteContentMove](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a><span data-ttu-id="b4eb2-158">Запуск перемещения географического расположения сайта SharePoint для сайта, подключенного к группе Office 365</span><span class="sxs-lookup"><span data-stu-id="b4eb2-158">Start a SharePoint site geo move for an Office 365 Group-connected site</span></span>

<span data-ttu-id="b4eb2-159">Чтобы переместить сайт, подключенный к группе Office 365, глобальный администратор должен сначала изменить атрибут предпочтительного расположения данных (PDL) для группы Office 365.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-159">To move an Office 365 Group-connected site, the global administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="b4eb2-160">Настройка атрибута PDL для группы Office 365:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-160">To set the PDL for an Office 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="b4eb2-161">После обновления атрибута PDL вы можете начать перемещение сайта:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-161">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="b4eb2-162">Отмена перемещения географического расположения сайта SharePoint</span><span class="sxs-lookup"><span data-stu-id="b4eb2-162">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="b4eb2-163">Перемещение географического расположения сайта SharePoint можно остановить, если этот процесс не находится на этапе выполнения или не завершен с помощью командлета `Stop-SPOSiteContentMove`.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-163">You can stop a SharePoint site geo move, provided the move is not in progress or completed by using the `Stop-SPOSiteContentMove` cmdlet.</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="b4eb2-164">Определение состояния перемещения географического расположения сайта SharePoint</span><span class="sxs-lookup"><span data-stu-id="b4eb2-164">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="b4eb2-165">Вы можете определить состояние перемещения сайта в отношении геообъекта (в расположение или из расположения), к которому подключены, с помощью следующих командлетов:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-165">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="b4eb2-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (сайты, не подключенные к группе)</span><span class="sxs-lookup"><span data-stu-id="b4eb2-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="b4eb2-167">Get-SPOUnifiedGroupMoveState (сайты, подключенные к группе)</span><span class="sxs-lookup"><span data-stu-id="b4eb2-167">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="b4eb2-168">Используйте параметр `-SourceSiteUrl`, чтобы указать сайт, для которого нужно просмотреть состояние перемещения.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-168">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="b4eb2-169">Состояния перемещения описаны в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-169">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="b4eb2-170">Состояние</span><span class="sxs-lookup"><span data-stu-id="b4eb2-170">Status</span></span>|<span data-ttu-id="b4eb2-171">Описание</span><span class="sxs-lookup"><span data-stu-id="b4eb2-171">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="b4eb2-172">Ready to Trigger</span><span class="sxs-lookup"><span data-stu-id="b4eb2-172">Ready to Trigger</span></span>|<span data-ttu-id="b4eb2-173">Перемещение не начато.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-173">The move has not started.</span></span>|
|<span data-ttu-id="b4eb2-174">Scheduled</span><span class="sxs-lookup"><span data-stu-id="b4eb2-174">Scheduled</span></span>|<span data-ttu-id="b4eb2-175">Перемещение в очереди, но еще не началось.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-175">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="b4eb2-176">InProgress (n/4)</span><span class="sxs-lookup"><span data-stu-id="b4eb2-176">InProgress (n/4)</span></span>|<span data-ttu-id="b4eb2-177">Перемещение в процессе и находится в одном из следующих состояний: "проверка" (1/4), "резервное копирование" (2/4), "восстановление" (3/4), "очистка" (4/4).</span><span class="sxs-lookup"><span data-stu-id="b4eb2-177">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="b4eb2-178">Success</span><span class="sxs-lookup"><span data-stu-id="b4eb2-178">Success</span></span>|<span data-ttu-id="b4eb2-179">Перемещение успешно завершено.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-179">The move has completed successfully.</span></span>|
|<span data-ttu-id="b4eb2-180">Failed</span><span class="sxs-lookup"><span data-stu-id="b4eb2-180">Failed</span></span>|<span data-ttu-id="b4eb2-181">Перемещение не удалось выполнить.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-181">The move failed.</span></span>|

<span data-ttu-id="b4eb2-182">Вы также можете применить параметр `-Verbose`, чтобы просмотреть дополнительные сведения о перемещении.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-182">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="b4eb2-183">Взаимодействие с пользователем</span><span class="sxs-lookup"><span data-stu-id="b4eb2-183">User experience</span></span>

<span data-ttu-id="b4eb2-184">Перемещение сайта в другой геообъект должно проходить максимально незаметно для пользователей сайта.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-184">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="b4eb2-185">Если не считать кратковременного состояния доступа только для чтения при перемещении, после завершения этого процесса существующие ссылки и разрешения будут доступны в обычном режиме.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-185">Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="b4eb2-186">Сайт</span><span class="sxs-lookup"><span data-stu-id="b4eb2-186">Site</span></span>

<span data-ttu-id="b4eb2-187">Во время перемещения сайт доступен только для чтения.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-187">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="b4eb2-188">Когда перемещение завершится, при попытке пользователя щелкнуть закладку или другую ссылку, ведущую к сайту, он будет направлен к новому сайту в новом географическом расположении.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-188">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="b4eb2-189">Разрешения</span><span class="sxs-lookup"><span data-stu-id="b4eb2-189">Permissions</span></span>

<span data-ttu-id="b4eb2-190">У пользователей с разрешениями для сайта будет к нему доступ во время перемещения и после его завершения.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-190">Users with permissions to site will continue to have access to the site during the move and after it's complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="b4eb2-191">Клиент синхронизации</span><span class="sxs-lookup"><span data-stu-id="b4eb2-191">Sync Client</span></span>

<span data-ttu-id="b4eb2-192">Когда будет выполнено перемещение сайта, клиент синхронизации автоматически обнаружит и легко перенесет синхронизацию в новое расположение сайта.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-192">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="b4eb2-193">Пользователю не нужно выполнять повторный вход или любые другие действия.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-193">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="b4eb2-194">(Требуется клиент синхронизации версии 17.3.6943.0625 или более поздней.)</span><span class="sxs-lookup"><span data-stu-id="b4eb2-194">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="b4eb2-195">Если пользователь попробует обновить файл во время перемещения, клиент синхронизации уведомит его о том, что отправка файла при выполнении перемещения приостанавливается.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-195">If a user updates a file while the move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="b4eb2-196">Предоставление ссылок</span><span class="sxs-lookup"><span data-stu-id="b4eb2-196">Sharing links</span></span>

<span data-ttu-id="b4eb2-197">Когда перемещение географического расположения сайта SharePoint будет завершено, для существующих предоставленных ссылок на перемещенные файлы будет автоматически выполняться перенаправление на новый геообъект.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-197">When the SharePoint site geo move completes, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="b4eb2-198">Недавно использованные файлы в Office (MRU)</span><span class="sxs-lookup"><span data-stu-id="b4eb2-198">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="b4eb2-199">Служба MRU обновляется с URL-адресом сайта и URL-адресами его содержимого после завершения перемещения.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-199">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="b4eb2-200">Это применяется к Word, Excel и PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-200">This applies to Word, Excel, and PowerPoint.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="b4eb2-201">Интерфейс OneNote</span><span class="sxs-lookup"><span data-stu-id="b4eb2-201">OneNote experience</span></span>

<span data-ttu-id="b4eb2-202">Когда перемещение сайта будет завершено, приложение UWP (универсальное) и клиент OneNote win32 автоматически обнаружат и легко синхронизируют записные книжки с новым расположением сайта.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-202">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="b4eb2-203">Пользователю не нужно выполнять повторный вход или любые другие действия.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-203">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="b4eb2-204">Во время выполнения перемещения сайта единственным отображаемым индикатором для пользователя является уведомление об ошибке синхронизации записной книжки.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-204">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="b4eb2-205">Эта возможность доступна для следующих клиентских версий OneNote:</span><span class="sxs-lookup"><span data-stu-id="b4eb2-205">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="b4eb2-206">OneNote win32 версии 16.0.8326.2096 (или более поздней);</span><span class="sxs-lookup"><span data-stu-id="b4eb2-206">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="b4eb2-207">OneNote UWP версии 16.0.8431.1006 (или более поздней);</span><span class="sxs-lookup"><span data-stu-id="b4eb2-207">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="b4eb2-208">приложение OneNote Mobile версии 16.0.8431.1011 (или более поздней).</span><span class="sxs-lookup"><span data-stu-id="b4eb2-208">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-office-365-group-connected-sites"></a><span data-ttu-id="b4eb2-209">Teams (применимо к сайтам, подключенным к группе Office 365)</span><span class="sxs-lookup"><span data-stu-id="b4eb2-209">Teams (applicable to Office 365 Group connected sites)</span></span>

<span data-ttu-id="b4eb2-210">Когда перемещение географического расположения сайта SharePoint будет завершено, пользователи получат доступ к файлам сайта, подключенного к группе Office 365, в приложении Teams.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-210">When the SharePoint site geo move completes, users will have access to their Office 365 Group site files on the Teams app.</span></span> <span data-ttu-id="b4eb2-211">Кроме того, файлы, отправленные из сайта через чат Teams до такого перемещения, будут продолжать работать и после него.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-211">Additionally, files shared via Teams chat from their site prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="b4eb2-212">Мобильное приложение SharePoint (iOS или Android)</span><span class="sxs-lookup"><span data-stu-id="b4eb2-212">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="b4eb2-213">Мобильное приложение SharePoint совместимо с переносом географических расположений и может определять новое географическое расположение сайта.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-213">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="b4eb2-214">Рабочие процессы SharePoint</span><span class="sxs-lookup"><span data-stu-id="b4eb2-214">SharePoint workflows</span></span>

<span data-ttu-id="b4eb2-215">Рабочие процессы SharePoint 2013 требуют повторной публикации после перемещения сайта.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-215">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="b4eb2-216">Рабочие процессы SharePoint 2010 должны продолжать нормально работать.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-216">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="b4eb2-217">Приложения</span><span class="sxs-lookup"><span data-stu-id="b4eb2-217">Apps</span></span>

<span data-ttu-id="b4eb2-218">Если вы перемещаете сайт с приложениями, необходимо повторно создать экземпляр приложения в новом географическом расположении сайта, так как приложение и его связи могут быть недоступны в конечном геообъекте.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-218">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="b4eb2-219">Flow</span><span class="sxs-lookup"><span data-stu-id="b4eb2-219">Flow</span></span>

<span data-ttu-id="b4eb2-220">В большинстве случаев потоки Flow будут продолжать работать после перемещения географического расположения сайта SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-220">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="b4eb2-221">Рекомендуется проверить их после завершения перемещения.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-221">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="b4eb2-222">PowerApps</span><span class="sxs-lookup"><span data-stu-id="b4eb2-222">PowerApps</span></span>

<span data-ttu-id="b4eb2-223">Для PowerApps требуется повторное создание в конечном расположении.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-223">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="b4eb2-224">Перемещение данных между географическими расположениями</span><span class="sxs-lookup"><span data-stu-id="b4eb2-224">Data movement between geo locations</span></span>

<span data-ttu-id="b4eb2-225">SharePoint использует хранилище BLOB-объектов Azure для своего содержимого, а метаданные, связанные с сайтами и файлами, хранятся в SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-225">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="b4eb2-226">После перемещения сайта из исходного в новое географическое расположение служба также переместит связанное хранилище BLOB-объектов.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-226">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="b4eb2-227">Перемещение хранилища BLOB-объектов завершается примерно за 40 дней.</span><span class="sxs-lookup"><span data-stu-id="b4eb2-227">Blob Storage moves complete in approximately 40 days.</span></span> 
