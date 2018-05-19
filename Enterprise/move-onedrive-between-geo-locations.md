---
title: Перемещение сайта OneDrive в другой геообъект
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
description: Сведения о перемещении сайта OneDrive в другой геообъект.
ms.openlocfilehash: 6bac98cc0707f977b7b585e8ae0a570f4b9662ee
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="f09af-103">Перемещение сайта OneDrive в другой геообъект</span><span class="sxs-lookup"><span data-stu-id="f09af-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="f09af-p101">С помощью функции перемещения OneDrive в отношении геообъекта можно переместить OneDrive пользователя в другое географическое расположение. Перемещение OneDrive в отношении геообъекта выполняет администратор SharePoint Online или глобальный администратор Office 365. Перед началом этого действия предупредите пользователя о переносе его OneDrive и посоветуйте ему закрыть все файлы на время выполнения перемещения. (Если во время перемещения будет открыт какой-либо документ пользователя в клиенте Office, после перемещения такой документ необходимо будет сохранить в новом расположении.) При необходимости перемещение можно запланировать на будущую дату.</span><span class="sxs-lookup"><span data-stu-id="f09af-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="f09af-p102">Для хранения содержимого служба OneDrive использует хранилище BLOB-объектов Azure. Хранилище BLOB-объектов, связанное с OneDrive пользователя, будет перемещено из исходного в целевой геообъект в течение 40 дней с того момента, как пользователю станет доступным OneDrive в целевом геообъекте. Доступ к OneDrive пользователя будет восстановлен сразу после того, как станет доступным OneDrive в целевом геообъекте.</span><span class="sxs-lookup"><span data-stu-id="f09af-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="f09af-p103">Пока открыто окно перемещения OneDrive в отношении геообъекта (около 2–6 часов), служба OneDrive пользователя доступна только для чтения. Пользователь по-прежнему сможет получить доступ к своим файлам с помощью клиента синхронизации OneDrive или на сайте OneDrive в SharePoint Online. После перемещения OneDrive в отношении геообъекта пользователь будет автоматически подключен к OneDrive в целевом географическом расположении, когда попробует перейти к OneDrive в средстве запуска приложений Office 365. Клиент синхронизации в новом расположении автоматически начнет синхронизацию.</span><span class="sxs-lookup"><span data-stu-id="f09af-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="f09af-115">Процедуры, описываемые в этой статье, требуют наличия [модуля Microsoft SharePoint Online для PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="f09af-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="f09af-116">Перемещение сайта OneDrive</span><span class="sxs-lookup"><span data-stu-id="f09af-116">Moving a OneDrive site</span></span>

<span data-ttu-id="f09af-p104">Чтобы выполнить перемещение OneDrive в отношении геообъекта, администратор клиента должен сначала задать предпочтительное расположение данных (PDL) пользователя. Указав PDL, подождите как минимум 24 часа, прежде чем приступать к перемещению OneDrive в отношении геообъекта. Это время отведено на синхронизацию обновления PDL между географическими расположениями.</span><span class="sxs-lookup"><span data-stu-id="f09af-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="f09af-119">Используя командлеты перемещения в отношении геообъекта, подключитесь к службе SPO в текущем географическом расположении OneDrive пользователя с помощью такого синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="f09af-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="f09af-120">Чтобы переместить, например, OneDrive пользователя matt@contosoenergy.onmicrosoft.com, подключитесь к европейскому Центру администрирования SharePoint, так как OneDrive пользователя находится в Европе.</span><span class="sxs-lookup"><span data-stu-id="f09af-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="f09af-121">Проверка среды</span><span class="sxs-lookup"><span data-stu-id="f09af-121">Validating the environment</span></span>

<span data-ttu-id="f09af-122">Прежде чем начинать перемещение OneDrive в отношении геообъекта, рекомендуем проверить среду.</span><span class="sxs-lookup"><span data-stu-id="f09af-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="f09af-123">Чтобы проверить, все ли геообъекты совместимы, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="f09af-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="f09af-p105">Переместить службу OneDrive невозможно, если она находится в состоянии удержания по юридическим причинам или содержит дочерний сайт. Чтобы проверить возможность перемещения OneDrive, выполните командлет Start-SPOUserAndContentMove с параметром -ValidationOnly.</span><span class="sxs-lookup"><span data-stu-id="f09af-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="f09af-p106">Если служба OneDrive готова к перемещению, вернется отклик, указывающий на успешное выполнение. Если же есть состояние удержания по юридическим причинам или дочерний сайт, что будет препятствовать перемещению, вернется отклик, указывающий на ошибку. Убедившись в том, что служба OneDrive готова к перемещению, начинайте эту процедуру.</span><span class="sxs-lookup"><span data-stu-id="f09af-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="f09af-128">Перемещение OneDrive в отношении геообъекта</span><span class="sxs-lookup"><span data-stu-id="f09af-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="f09af-129">Чтобы начать перемещение, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="f09af-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="f09af-130">Используйте эти параметры:</span><span class="sxs-lookup"><span data-stu-id="f09af-130">Using these parameters:</span></span>

-   <span data-ttu-id="f09af-131">_UserPrincipalName_ — имя участника-пользователя, OneDrive которого перемещается.</span><span class="sxs-lookup"><span data-stu-id="f09af-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="f09af-p107">_DestinationDataLocation_ — геообъект, куда следует переместить OneDrive. Он должен совпадать с предпочтительным расположением данных пользователя.</span><span class="sxs-lookup"><span data-stu-id="f09af-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="f09af-134">Прежде чем начинать перемещение OneDrive в отношении геообъекта, рекомендуем запустить `Get-SPOGeoMoveStateCompatibility` с параметром `ValidationOnly`.</span><span class="sxs-lookup"><span data-stu-id="f09af-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="f09af-135">Например, чтобы переместить OneDrive matt@contosoenergy.onmicrosoft.com из Европы в Австралию, выполните такую команду:</span><span class="sxs-lookup"><span data-stu-id="f09af-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="f09af-136">Чтобы запланировать перемещение в отношении геообъекта на более позднее время, используйте один из следующих параметров:</span><span class="sxs-lookup"><span data-stu-id="f09af-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="f09af-p108">_PreferredMoveBeginDate_ — предполагаемое время начала перемещения. Должно быть задано в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="f09af-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="f09af-p109">_PreferredMoveEndDate_ — предполагаемое время завершения перемещения (самый короткий период). Должно быть задано в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="f09af-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="f09af-141">Отмена перемещения OneDrive в отношении геообъекта</span><span class="sxs-lookup"><span data-stu-id="f09af-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="f09af-142">Перемещение OneDrive пользователя в отношении геообъекта можно остановить, если этот процесс не находится на этапе выполнения или не завершен с помощью такого командлета:</span><span class="sxs-lookup"><span data-stu-id="f09af-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="f09af-143">Здесь _UserPrincipalName_ — имя участника-пользователя, перемещение OneDrive которого нужно остановить.</span><span class="sxs-lookup"><span data-stu-id="f09af-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="f09af-144">Определение текущего состояния</span><span class="sxs-lookup"><span data-stu-id="f09af-144">Determining current status</span></span>

<span data-ttu-id="f09af-145">С помощью командлета Get-SPOUserAndContentMoveState вы можете проверить состояние перемещения OneDrive в отношении геообъекта (в расположение или из расположения), к которому подключены.</span><span class="sxs-lookup"><span data-stu-id="f09af-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="f09af-146">Состояния перемещения описаны в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="f09af-146">The fields in alerts are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f09af-147"><strong>Состояние</strong></span><span class="sxs-lookup"><span data-stu-id="f09af-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="f09af-148"><strong>Описание</strong></span><span class="sxs-lookup"><span data-stu-id="f09af-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f09af-149">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f09af-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="f09af-150">Перемещение не начато.</span><span class="sxs-lookup"><span data-stu-id="f09af-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f09af-151">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="f09af-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="f09af-152">Перемещение в процессе и находится в одном из следующих состояний: "проверка" (1/4), "резервное копирование" (2/4), "восстановление" (3/4), "очистка" (4/4).</span><span class="sxs-lookup"><span data-stu-id="f09af-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f09af-153">Success</span><span class="sxs-lookup"><span data-stu-id="f09af-153">Success</span></span></td>
<td align="left"><span data-ttu-id="f09af-154">Перемещение успешно завершено.</span><span class="sxs-lookup"><span data-stu-id="f09af-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f09af-155">Failed</span><span class="sxs-lookup"><span data-stu-id="f09af-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="f09af-156">Перемещение не удалось выполнить.</span><span class="sxs-lookup"><span data-stu-id="f09af-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f09af-157">Чтобы найти состояние перемещения определенного пользователя, используйте параметр UserPrincipalName.</span><span class="sxs-lookup"><span data-stu-id="f09af-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="f09af-158">Чтобы найти состояние всех перемещений в геообъект или из геообъекта, к которому вы подключены, используйте параметр MoveState с одним из следующих значений: NotStarted, InProgress, Success, Failed, All.</span><span class="sxs-lookup"><span data-stu-id="f09af-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="f09af-159">Для более подробного описания состояния перемещения вы можете добавить параметр `-Verbose`.</span><span class="sxs-lookup"><span data-stu-id="f09af-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="f09af-160">Взаимодействие с пользователем</span><span class="sxs-lookup"><span data-stu-id="f09af-160">User Experience</span></span>

<span data-ttu-id="f09af-p110">Перемещение OneDrive пользователей в другой геообъект должно проходить максимально незаметно для них. Если не считать кратковременного состояния доступа только для чтения при перемещении, после завершения этого процесса существующие ссылки и разрешения будут доступны в обычном режиме.</span><span class="sxs-lookup"><span data-stu-id="f09af-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="f09af-163">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="f09af-163">OneDrive for Business</span></span>

<span data-ttu-id="f09af-p111">Во время перемещения служба OneDrive пользователя доступна только для чтения. Когда перемещение завершится, при попытке пользователя перейти к OneDrive в средстве запуска приложений Office 365 или веб-браузере он будет направлен к OneDrive в новом географическом расположении.</span><span class="sxs-lookup"><span data-stu-id="f09af-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="f09af-166">Разрешения для содержимого OneDrive</span><span class="sxs-lookup"><span data-stu-id="f09af-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="f09af-167">У пользователей с разрешениями для содержимого OneDrive будет к нему доступ во время перемещения и после его завершения.</span><span class="sxs-lookup"><span data-stu-id="f09af-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="f09af-168">Клиент синхронизации OneDrive</span><span class="sxs-lookup"><span data-stu-id="f09af-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="f09af-p112">Когда будет выполнено перемещение OneDrive в отношении геообъекта, клиент синхронизации OneDrive автоматически обнаружит и легко перенесет синхронизацию в новое расположение OneDrive. Пользователю не нужно выполнять повторный вход или любые другие действия.</span><span class="sxs-lookup"><span data-stu-id="f09af-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="f09af-171">Если пользователь попробует обновить файл во время перемещения OneDrive в отношении геообъекта, клиент синхронизации уведомит его о том, что отправка файла при выполнении перемещения приостанавливается.</span><span class="sxs-lookup"><span data-stu-id="f09af-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="f09af-172">Предоставление ссылок</span><span class="sxs-lookup"><span data-stu-id="f09af-172">Sharing links</span></span> 

<span data-ttu-id="f09af-173">Когда перемещение OneDrive в отношении геообъекта будет завершено, для существующих предоставленных ссылок на перемещенные файлы будет автоматически выполняться перенаправление на новый геообъект.</span><span class="sxs-lookup"><span data-stu-id="f09af-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="f09af-174">Интерфейс OneNote</span><span class="sxs-lookup"><span data-stu-id="f09af-174">OneNote Experience</span></span> 

<span data-ttu-id="f09af-p113">Когда перемещение OneDrive в отношении геообъекта будет завершено, приложение UWP (универсальное) и клиент OneNote win32 автоматически обнаружат и легко синхронизируют записные книжки с новым расположением OneDrive. Пользователю не нужно будет выполнять повторный вход или любые другие действия. Во время выполнения перемещения OneDrive в отношении геообъекта единственным отображаемым индикатором для пользователя является уведомление об ошибке синхронизации записной книжки. Эта возможность доступна для следующих клиентских версий OneNote:</span><span class="sxs-lookup"><span data-stu-id="f09af-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="f09af-179">OneNote win32 версии 16.0.8326.2096 (или более поздней);</span><span class="sxs-lookup"><span data-stu-id="f09af-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="f09af-180">OneNote UWP версии 16.0.8431.1006 (или более поздней);</span><span class="sxs-lookup"><span data-stu-id="f09af-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="f09af-181">приложение OneNote Mobile версии 16.0.8431.1011 (или более поздней).</span><span class="sxs-lookup"><span data-stu-id="f09af-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="f09af-182">Приложение Teams</span><span class="sxs-lookup"><span data-stu-id="f09af-182">Teams app</span></span>

<span data-ttu-id="f09af-p114">Когда перемещение OneDrive в отношении геообъекта будет завершено, пользователи получат доступ к своим файлам OneDrive в приложении Teams. Кроме того, файлы, отправленные из OneDrive через чат Teams до такого перемещения, будут продолжать работать и после него.</span><span class="sxs-lookup"><span data-stu-id="f09af-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="f09af-185">Мобильное приложение OneDrive для бизнеса (iOS)</span><span class="sxs-lookup"><span data-stu-id="f09af-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="f09af-186">Когда перемещение OneDrive в отношении геообъекта будет завершено, пользователю понадобится выйти из мобильного приложения для iOS и снова войти в него. Благодаря этому будет выполнена синхронизация с новым расположением OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f09af-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="f09af-187">Существующие отслеживаемые группы и сайты</span><span class="sxs-lookup"><span data-stu-id="f09af-187">Existing followed groups and sites</span></span>

<span data-ttu-id="f09af-p115">Отслеживаемые сайты и группы будут отображаться в учетной записи OneDrive для бизнеса пользователя независимо от его географического расположения. Сайты и группы, размещенные в другом геообъекте, откроются на отдельной вкладке.</span><span class="sxs-lookup"><span data-stu-id="f09af-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
