---
title: Перемещение сайта OneDrive различных географического расположения
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Узнайте, как для переноса сайта OneDrive в разных географического расположения.
ms.openlocfilehash: a31f683170fdb83dac90e9d09884c3020d1a47b1
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="90a02-103">Перемещение сайта OneDrive различных географического расположения</span><span class="sxs-lookup"><span data-stu-id="90a02-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="90a02-p101">С помощью OneDrive переместить географически, можно переместить пользователя OneDrive в разных географического расположения. Перемещение географически OneDrive производится администратору SharePoint Online или глобального администратора Office 365. Прежде чем начать OneDrive, географически перемещение, убедитесь, что для уведомления пользователей, чьи OneDrive перемещается и рекомендуем они закрыть все файлы во время выполнения перемещения. (Если у пользователя есть документ открыт, с помощью клиента Office во время перемещения, затем на перемещение завершение работы необходимые документ будет сохранен в новом расположении). Перемещение можно запланировать на время в будущем, если это необходимо.</span><span class="sxs-lookup"><span data-stu-id="90a02-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="90a02-p102">Служба OneDrive использует хранилище больших двоичных объектов Azure для хранения содержимого. Хранение больших двоичных объектов, связанных со службой OneDrive пользователя будут перемещены из источника в месте назначения географически в пределах 40 дням назначения OneDrive, доступные для пользователя. Доступ к OneDrive пользователя будут восстановлены сразу же назначения OneDrive доступен.</span><span class="sxs-lookup"><span data-stu-id="90a02-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="90a02-p103">Во время перемещения географически OneDrive окно (около 2 – 6 часов) OneDrive пользователя имеет значение только для чтения. Пользователь по-прежнему можно получить доступ к их файлы с помощью клиента синхронизации OneDrive или их OneDrive сайта в SharePoint Online. После завершения перемещения географически OneDrive пользователя будет автоматически подключены к их OneDrive в месте назначения географически при переходе в OneDrive запуска приложения для Office 365. Клиент синхронизации автоматически начнется синхронизация из нового расположения.</span><span class="sxs-lookup"><span data-stu-id="90a02-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="90a02-115">Процедуры, описанные в этой статье требуется [Модуль Microsoft SharePoint Online PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="90a02-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="90a02-116">Перемещение сайта OneDrive</span><span class="sxs-lookup"><span data-stu-id="90a02-116">Moving a OneDrive site</span></span>

<span data-ttu-id="90a02-p104">Для выполнения OneDrive переместить географически, администратор клиента нужно задать расположение предпочитаемое данных пользователя (PDL) соответствующие географического расположения. После задания PDL дождитесь менее 24 часа в качестве обновления PDL для синхронизации в подразделениях географически перед началом работы move географически OneDrive.</span><span class="sxs-lookup"><span data-stu-id="90a02-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="90a02-119">Если с помощью географически переместить командлеты, подключения к службе SPO пользователя текущей позиции OneDrive географически, используя следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="90a02-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="90a02-120">Например: перемещение OneDrive пользователя «Matt@contosoenergy.onmicrosoft.com» подключиться к центра администрирования SharePoint ЕВРО как OneDrive пользователя находится в ЕВРО географического расположения:</span><span class="sxs-lookup"><span data-stu-id="90a02-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="90a02-121">Проверка среды</span><span class="sxs-lookup"><span data-stu-id="90a02-121">Validating the environment</span></span>

<span data-ttu-id="90a02-122">Прежде чем начать перемещение географически OneDrive, рекомендуется проверить среды.</span><span class="sxs-lookup"><span data-stu-id="90a02-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="90a02-123">Чтобы обеспечить совместимость все географического расположения, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="90a02-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="90a02-p105">Если OneDrive в разделе удержания по юридическим причинам или дочернего сайта, его нельзя перемещать. Командлет Start-SPOUserAndContentMove совместно с параметром - ValidationOnly для проверки, если OneDrive может быть перемещен:</span><span class="sxs-lookup"><span data-stu-id="90a02-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="90a02-p106">Это возвращает успех, если OneDrive готова к перемещены или ошибкой, если удержания по юридическим причинам или дочернего сайта, который будет препятствовать move. После проверки, что OneDrive готова для перемещения можно начать перемещение.</span><span class="sxs-lookup"><span data-stu-id="90a02-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="90a02-128">Начать перемещение географически OneDrive</span><span class="sxs-lookup"><span data-stu-id="90a02-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="90a02-129">Чтобы запустить move, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="90a02-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="90a02-130">Используя следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="90a02-130">Using these parameters:</span></span>

-   <span data-ttu-id="90a02-131">_UserPrincipalName_ — имя участника-пользователя, чьи OneDrive перемещается.</span><span class="sxs-lookup"><span data-stu-id="90a02-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="90a02-p107">_DestinationDataLocation_ – географического расположения, где OneDrive нужно переместить. Это должен быть такой же, как расположение предпочитаемый данных пользователя.</span><span class="sxs-lookup"><span data-stu-id="90a02-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="90a02-134">Мы рекомендуем running `Get-SPOGeoMoveStateCompatibility` с `ValidationOnly` до инициализации OneDrive перемещение географически.</span><span class="sxs-lookup"><span data-stu-id="90a02-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="90a02-135">Например чтобы переместить OneDrive matt@contosoenergy.onmicrosoft.com из ЕВРО Стандартное, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="90a02-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="90a02-136">Для планирования перемещения географически для последующего, используйте один из следующих параметров:</span><span class="sxs-lookup"><span data-stu-id="90a02-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="90a02-137">_PreferredMoveBeginDate_ – скорее move начинается с этой указанное время.</span><span class="sxs-lookup"><span data-stu-id="90a02-137">_PreferredMoveBeginDate_ – The move will likely begin at this specified time.</span></span>

-   <span data-ttu-id="90a02-138">_PreferredMoveEndDate_ – скорее перемещения закончится в этот указанное время наиболее объем работ по отдельности.</span><span class="sxs-lookup"><span data-stu-id="90a02-138">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis.</span></span>

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="90a02-139">Отменить перемещение географически OneDrive</span><span class="sxs-lookup"><span data-stu-id="90a02-139">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="90a02-140">Можно остановить переместить географически OneDrive пользователя, предоставляемые move не выполняется или завершено с помощью командлета:</span><span class="sxs-lookup"><span data-stu-id="90a02-140">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="90a02-141">Где _UserPrincipalName_ — это имя участника-пользователя, которого OneDrive переместить почтовые требуется остановить.</span><span class="sxs-lookup"><span data-stu-id="90a02-141">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="90a02-142">Определение текущего состояния</span><span class="sxs-lookup"><span data-stu-id="90a02-142">Determining current status</span></span>

<span data-ttu-id="90a02-143">Можно проверить состояние OneDrive, географически перемещение и выход географически, установлено подключение с помощью командлета Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="90a02-143">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="90a02-144">На перемещение состояния, описаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="90a02-144">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="90a02-145"><strong>Status</strong></span><span class="sxs-lookup"><span data-stu-id="90a02-145"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="90a02-146"><strong>Описание</strong></span><span class="sxs-lookup"><span data-stu-id="90a02-146"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="90a02-147">NotStarted</span><span class="sxs-lookup"><span data-stu-id="90a02-147">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="90a02-148">Перемещение не запущена.</span><span class="sxs-lookup"><span data-stu-id="90a02-148">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="90a02-149">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="90a02-149">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="90a02-150">Перемещение находится в стадии разработки в одном из следующих состояний: проверки (1/4), резервное копирование (2/4), восстановить (3 и 4) очистки (4/4).</span><span class="sxs-lookup"><span data-stu-id="90a02-150">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="90a02-151">Success (Успешно)</span><span class="sxs-lookup"><span data-stu-id="90a02-151">Success</span></span></td>
<td align="left"><span data-ttu-id="90a02-152">Перемещение успешно завершена.</span><span class="sxs-lookup"><span data-stu-id="90a02-152">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="90a02-153">Failed</span><span class="sxs-lookup"><span data-stu-id="90a02-153">Failed</span></span></td>
<td align="left"><span data-ttu-id="90a02-154">Не удалось переместить.</span><span class="sxs-lookup"><span data-stu-id="90a02-154">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="90a02-155">Чтобы найти состояния перемещения определенного пользователя, используйте параметр UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="90a02-155">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="90a02-156">Чтобы найти состояние всех перемещений в данные группы или из расположения географически, вы подключены к, используйте параметр MoveState с одним из следующих значений: NotStarted, InProgress, успех, не удалось выполнить, все.</span><span class="sxs-lookup"><span data-stu-id="90a02-156">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="90a02-157">Также можно добавить `-Verbose` параметр более подробное описание перемещения состояния.</span><span class="sxs-lookup"><span data-stu-id="90a02-157">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="90a02-158">Удобство пользователя</span><span class="sxs-lookup"><span data-stu-id="90a02-158">User Experience</span></span>

<span data-ttu-id="90a02-p108">Пользователи OneDrive следует заметить мешая при перемещении их OneDrive для разных географического расположения. Помимо краткое состояние только для чтения во время перемещения существующие связи и разрешения будет продолжать работать неправильно после завершения перемещения.</span><span class="sxs-lookup"><span data-stu-id="90a02-p108">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="90a02-161">OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="90a02-161">OneDrive for Business</span></span>

<span data-ttu-id="90a02-p109">В процессе перемещения пользователя OneDrive имеет значение только для чтения. После завершения перемещения пользователь перенаправляется на их OneDrive в новом расположении географически, когда они переходят в OneDrive запуска приложения для Office 365 или веб-браузера.</span><span class="sxs-lookup"><span data-stu-id="90a02-p109">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="90a02-164">Разрешения на OneDrive содержимого</span><span class="sxs-lookup"><span data-stu-id="90a02-164">Permissions on OneDrive content</span></span>

<span data-ttu-id="90a02-165">Пользователи с разрешениями на OneDrive содержимого будет иметь доступ к содержимому во время перемещения и после завершения.</span><span class="sxs-lookup"><span data-stu-id="90a02-165">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="90a02-166">Клиент синхронизации OneDrive</span><span class="sxs-lookup"><span data-stu-id="90a02-166">OneDrive Sync Client</span></span> 

<span data-ttu-id="90a02-p110">Клиента синхронизации OneDrive автоматически определяет и легко перенести синхронизации в новом расположении OneDrive после завершения перемещения географически OneDrive. Пользователь не требуется входить в систему и выполнения других действий.</span><span class="sxs-lookup"><span data-stu-id="90a02-p110">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="90a02-169">Если пользователь обновляет файл в процессе перемещения географически OneDrive, клиент синхронизации уведомим им, что имеются ожидающие передачи файлов во время перемещения.</span><span class="sxs-lookup"><span data-stu-id="90a02-169">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="90a02-170">Совместное использование ссылок</span><span class="sxs-lookup"><span data-stu-id="90a02-170">Sharing links</span></span> 

<span data-ttu-id="90a02-171">После географически OneDrive перемещение завершения, существующей общей ссылки для файлов, которые были перемещены автоматически перенаправляются на новое расположение географически.</span><span class="sxs-lookup"><span data-stu-id="90a02-171">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="90a02-172">Возможности OneNote</span><span class="sxs-lookup"><span data-stu-id="90a02-172">OneNote Experience</span></span> 

<span data-ttu-id="90a02-p111">Клиент OneNote win32 и UWP (универсальные) приложение будет автоматическое определение и эффективно синхронизировать записные книжки к новому местоположению OneDrive после завершения перемещения географически OneDrive. Пользователь не требуется входить в систему и выполнения других действий. Индикатор доступны только для пользователя — синхронизации записную книжку не будут выполнены при перемещении географически OneDrive находится в стадии разработки. Этот интерфейс доступна в следующих версиях клиента OneNote:</span><span class="sxs-lookup"><span data-stu-id="90a02-p111">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="90a02-177">Win32 OneNote – версии 16.0.8326.2096 (и более поздних версий)</span><span class="sxs-lookup"><span data-stu-id="90a02-177">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="90a02-178">UWP OneNote – версии 16.0.8431.1006 (и более поздних версий)</span><span class="sxs-lookup"><span data-stu-id="90a02-178">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="90a02-179">Приложение OneNote Mobile – версии 16.0.8431.1011 (и более поздних версий)</span><span class="sxs-lookup"><span data-stu-id="90a02-179">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="90a02-180">Приложение группы</span><span class="sxs-lookup"><span data-stu-id="90a02-180">Teams app</span></span>

<span data-ttu-id="90a02-p112">После географически OneDrive перемещение завершения, пользователи получат доступ к их файлы OneDrive на app. групп Кроме того, совместно с помощью чата группы из их OneDrive до перемещения географически файлы будут работать после завершения перемещения.</span><span class="sxs-lookup"><span data-stu-id="90a02-p112">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="90a02-183">OneDrive для мобильного бизнес-приложения (операций ввода-вывода)</span><span class="sxs-lookup"><span data-stu-id="90a02-183">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="90a02-184">После географически OneDrive перемещение завершения, пользователь должен выйти из системы и повторного входа на iOS мобильного приложения для синхронизации в новом расположении OneDrive.</span><span class="sxs-lookup"><span data-stu-id="90a02-184">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="90a02-185">Существующие за групп и веб-узлы</span><span class="sxs-lookup"><span data-stu-id="90a02-185">Existing followed groups and sites</span></span>

<span data-ttu-id="90a02-p113">Число сайтов и группы будут отображаться в пользователя OneDrive для бизнеса независимо от их географического расположения. Сайты и группы, находящиеся в другом месте географически будет открыт в отдельной вкладке.</span><span class="sxs-lookup"><span data-stu-id="90a02-p113">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
