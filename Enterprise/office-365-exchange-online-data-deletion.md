---
title: Удаление данных в Office 365 Exchange Online
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Как мягкое и жесткое удаление данных обрабатывается в Exchange Online.
ms.openlocfilehash: f25f2416778f19f8b2e464e31e6116a81eb872cc
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067788"
---
# <a name="exchange-online-data-deletion-in-office-365"></a><span data-ttu-id="69286-103">Удаление данных Exchange Online в Office 365</span><span class="sxs-lookup"><span data-stu-id="69286-103">Exchange Online Data Deletion in Office 365</span></span>
<span data-ttu-id="69286-104">В Exchange Online существует два типа удалений: "обратимое удаление" и "окончательное удаление".</span><span class="sxs-lookup"><span data-stu-id="69286-104">Within Exchange Online, there are two kinds of deletions: soft deletions and hard deletions.</span></span> <span data-ttu-id="69286-105">Это относится как к почтовым ящикам, так и к элементам в почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="69286-105">This applies to both mailboxes and items within a mailbox.</span></span>

## <a name="soft-deleted-and-hard-deleted-mailboxes"></a><span data-ttu-id="69286-106">Обратимо удаленные и обратимо удаленные почтовые ящики</span><span class="sxs-lookup"><span data-stu-id="69286-106">Soft-Deleted and Hard-Deleted Mailboxes</span></span>
<span data-ttu-id="69286-107">Обратимо удаленный почтовый ящик пользователя — это почтовый ящик, который был удален с помощью центра администрирования Microsoft 365 или командлета Recycle-Mailbox и все еще находился в корзине Azure Active Directory в течение менее 30 дней.</span><span class="sxs-lookup"><span data-stu-id="69286-107">A soft-deleted user mailbox is a mailbox that has been deleted using the Microsoft 365 admin center or the Remove-Mailbox cmdlet and has still been in the Azure Active Directory recycle bin for less than 30 days.</span></span> <span data-ttu-id="69286-108">Почтовые ящики могут быть обратимо удалены одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="69286-108">A mailbox can become soft-deleted in any of the following ways:</span></span>
- <span data-ttu-id="69286-109">Учетная запись пользователя Azure Active Directory, сопоставленная с почтовым ящиком пользователя, удалена с возможностью восстановления (объект пользователя находится вне области или в контейнере корзины).</span><span class="sxs-lookup"><span data-stu-id="69286-109">The user mailbox's associated Azure Active Directory user account is soft-deleted (the user object is out of scope or in the recycle bin container).</span></span>
- <span data-ttu-id="69286-110">Учетная запись пользователя Azure Active Directory, сопоставленная с почтовым ящиком пользователя, была окончательно удалена, но почтовый ящик Exchange Online находится в режиме хранения для судебного разбирательства или удержания электронных данных.</span><span class="sxs-lookup"><span data-stu-id="69286-110">The user mailbox's associated Azure Active Directory user account has been hard-deleted but the Exchange Online mailbox is under a litigation hold or eDiscovery hold.</span></span>
- <span data-ttu-id="69286-111">Учетная запись пользователя Azure Active Directory, сопоставленная с почтовым ящиком пользователя, была удалена в течение последних 30 дней; Максимальная длина хранения в Exchange Online будет храниться в обратимо удаленном состоянии, прежде чем оно будет необратимо очищено.</span><span class="sxs-lookup"><span data-stu-id="69286-111">The user mailbox's associated Azure Active Directory user account has been purged within the last 30 days; which is the maximum retention length Exchange Online will keep the mailbox in a soft-deleted state before it is permanently purged and unrecoverable.</span></span>

<span data-ttu-id="69286-112">Обратимо удаленный почтовый ящик пользователя — это почтовый ящик, который был удален одним из указанных ниже способов.</span><span class="sxs-lookup"><span data-stu-id="69286-112">A hard-deleted user mailbox is a mailbox that has been deleted in one of the following ways:</span></span>
- <span data-ttu-id="69286-113">Почтовый ящик пользователя был обратимо удален в течение более 30 дней, а связанный с ним пользователь Azure Active Directory был окончательно удален.</span><span class="sxs-lookup"><span data-stu-id="69286-113">The user mailbox has been soft-deleted for more than 30 days, and the associated Azure Active Directory user has been hard-deleted.</span></span> <span data-ttu-id="69286-114">Все содержимое почтового ящика, например сообщения электронной почты, контакты и файлы, удаляются без возможности восстановления.</span><span class="sxs-lookup"><span data-stu-id="69286-114">All mailbox content such as emails, contacts and files are permanently deleted.</span></span>
- <span data-ttu-id="69286-115">Учетная запись пользователя, связанная с почтовым ящиком пользователя, была окончательно удалена из Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="69286-115">The user account associated with the user mailbox has been hard-deleted from the Azure Active Directory.</span></span> <span data-ttu-id="69286-116">Почтовый ящик пользователя теперь является обратимым удалением в Exchange Online и остается в обратимо удаленном состоянии в течение 30 дней.</span><span class="sxs-lookup"><span data-stu-id="69286-116">The user mailbox is now soft-deleted in Exchange Online and stays in a soft-deleted state for 30 days.</span></span> <span data-ttu-id="69286-117">Если в течение 30 дней новый пользователь Azure Active Directory синхронизируется с исходной учетной записью получателя с тем же **ExchangeGuid** или **свойств archiveguid**и что новая учетная запись лицензируется для Exchange Online, это приведет к удаленному удалению исходный почтовый ящик пользователя.</span><span class="sxs-lookup"><span data-stu-id="69286-117">If in the 30-day period a new Azure Active Directory user is synchronized from the original recipient account with the same **ExchangeGuid** or **ArchiveGuid**, and that new account is licensed for Exchange Online, this will result in a hard deletion of the original user mailbox.</span></span> <span data-ttu-id="69286-118">Все содержимое почтового ящика, например сообщения электронной почты, контакты и файлы, удаляются без возможности восстановления.</span><span class="sxs-lookup"><span data-stu-id="69286-118">All mailbox content such as emails, contacts and files are permanently deleted.</span></span>
- <span data-ttu-id="69286-119">Обратимо удаленный почтовый ящик удаляется с помощью **Remove-Mailbox-PermanentlyDelete**.</span><span class="sxs-lookup"><span data-stu-id="69286-119">A soft-deleted mailbox is deleted using **Remove-Mailbox -PermanentlyDelete**.</span></span>

<span data-ttu-id="69286-120">В приведенных выше сценариях удаления предполагается, что почтовый ящик пользователя не находится в состоянии удержания, например в случае хранения для судебного разбирательства или удержания электронных данных.</span><span class="sxs-lookup"><span data-stu-id="69286-120">The above deletion scenarios assume that the user mailbox isn't in any of the hold states, like Litigation hold or eDiscovery hold.</span></span> <span data-ttu-id="69286-121">Если почтовый ящик имеет любой тип удержания, почтовый ящик удалить невозможно.</span><span class="sxs-lookup"><span data-stu-id="69286-121">If there is any type of hold on the mailbox, then the mailbox can't be deleted.</span></span> <span data-ttu-id="69286-122">Для всех типов получателей почты все параметры [хранения](https://support.office.com/article/manage-legal-investigations-in-office-365-2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e?ui=en-US&rs=en-US&ad=US) игнорируются и не оказывают влияния на принудительное удаление или обратимое удаление.</span><span class="sxs-lookup"><span data-stu-id="69286-122">For all mail-user recipient types, any [Hold](https://support.office.com/article/manage-legal-investigations-in-office-365-2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e?ui=en-US&rs=en-US&ad=US) settings are ignored and have no effect on hard-deletions or soft-deletions.</span></span>

## <a name="soft-deleted-and-hard-deleted-items"></a><span data-ttu-id="69286-123">Обратимо удаленные и обратимо удаленные элементы</span><span class="sxs-lookup"><span data-stu-id="69286-123">Soft-Deleted and Hard-Deleted Items</span></span>
<span data-ttu-id="69286-124">При удалении пользователем элемента почтового ящика (например, сообщения электронной почты, контакта, встречи календаря или задачи) элемент перемещается в папку "элементы с возможностью восстановления" и в вложенную папку с именем "удаления".</span><span class="sxs-lookup"><span data-stu-id="69286-124">When a user deletes a mailbox item (such as an email message, a contact, a calendar appointment, or a task), the item is moved to the Recoverable Items folder, and into a subfolder named "Deletions".</span></span> <span data-ttu-id="69286-125">Это называется обратимым удалением.</span><span class="sxs-lookup"><span data-stu-id="69286-125">This is referred to as a soft deletion.</span></span> <span data-ttu-id="69286-126">Срок хранения удаленных элементов в папке Удаленные зависит от периода хранения удаленных элементов, настроенного для почтового ящика.</span><span class="sxs-lookup"><span data-stu-id="69286-126">How long deleted items are kept in the Deletions folder depends on the deleted item retention period that is set for the mailbox.</span></span> <span data-ttu-id="69286-127">Почтовый ящик Exchange Online по умолчанию сохраняет удаленные элементы в течение 14 дней, но администраторы Exchange Online могут изменить этот параметр, чтобы увеличить период до 30 дней.</span><span class="sxs-lookup"><span data-stu-id="69286-127">An Exchange Online mailbox keeps deleted items for 14 days by default, but Exchange Online administrators can change this setting to increase the period up to a maximum of 30 days.</span></span> <span data-ttu-id="69286-128">(Подробное описание действий по увеличению срока хранения удаленных элементов для почтового ящика Exchange Online показано в разделе [изменение срока хранения безвозвратно удаленных элементов для почтового ящика Exchange Online](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention).) Пользователи могут восстанавливать или очищать удаленные элементы до истечения срока хранения для удаленного элемента.</span><span class="sxs-lookup"><span data-stu-id="69286-128">(For detailed steps to increase the deleted item retention period for an Exchange Online mailbox, see [Change how long permanently deleted items are kept for an Exchange Online mailbox](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention).) Users can recover, or purge, deleted items before the retention time for a deleted item expires.</span></span> <span data-ttu-id="69286-129">Для этого они используют функцию восстановления удаленных элементов в Microsoft Outlook или Outlook в Интернете.</span><span class="sxs-lookup"><span data-stu-id="69286-129">To do so, they use the Recover Deleted Items feature in Microsoft Outlook or Outlook on the web.</span></span>

<span data-ttu-id="69286-130">Если пользователь удаляет удаленный элемент с помощью функции восстановления удаленных элементов в Outlook или Outlook в Интернете, это называется окончательным удалением.</span><span class="sxs-lookup"><span data-stu-id="69286-130">If a user purges a deleted item by using the Recover Deleted Items feature in Outlook or Outlook on the web, this is known as a hard deletion.</span></span> <span data-ttu-id="69286-131">В Exchange Online восстановление отдельных элементов включается по умолчанию при создании нового почтового ящика, поэтому администратор по-прежнему может [восстанавливать](https://docs.microsoft.com/Exchange/recipients/user-mailboxes/recover-deleted-messages) удаленные элементы до истечения срока хранения удаленных элементов.</span><span class="sxs-lookup"><span data-stu-id="69286-131">In Exchange Online, single item recovery is enabled by default when a new mailbox is created, so an administrator can still [recover](https://docs.microsoft.com/Exchange/recipients/user-mailboxes/recover-deleted-messages) hard-deleted items before the deleted item retention period expires.</span></span> <span data-ttu-id="69286-132">Кроме того, если сообщение изменяется пользователем или процессом, копии исходного элемента также сохраняются при включении восстановления отдельных элементов.</span><span class="sxs-lookup"><span data-stu-id="69286-132">Also, if a message is changed by a user or a process, copies of the original item are also retained when single item recovery is enabled.</span></span>

## <a name="page-zeroing"></a><span data-ttu-id="69286-133">Обнуление страниц</span><span class="sxs-lookup"><span data-stu-id="69286-133">Page Zeroing</span></span>
<span data-ttu-id="69286-134">*Обнуление* — это механизм обеспечения безопасности, который записывает нулевые или двоичные шаблоны по отношению к удаленным данным, чтобы восстановить удаленные данные более сложно.</span><span class="sxs-lookup"><span data-stu-id="69286-134">*Zeroing* is a security mechanism that writes either zeros or a binary pattern over deleted data so that the deleted data is more difficult to recover.</span></span> <span data-ttu-id="69286-135">В Exchange Online базы данных почтовых ящиков используют *страницы* в качестве единиц хранения и реализуют процесс перезаписи, называемый *обнулением страниц*.</span><span class="sxs-lookup"><span data-stu-id="69286-135">In Exchange Online, mailbox databases use *pages* as their unit of storage, and implement an overwriting process called *page zeroing*.</span></span> <span data-ttu-id="69286-136">Обнуление страниц включено по умолчанию и не может быть отключено клиентами или корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="69286-136">Page zeroing is enabled by default, and it cannot be disabled by customers or by Microsoft.</span></span> <span data-ttu-id="69286-137">Операции обнуления страниц записываются в файлы журнала транзакций, поэтому все копии этой базы данных будут обнулены одинаковым образом.</span><span class="sxs-lookup"><span data-stu-id="69286-137">Page zeroing operations are recorded in the transaction log files so that all copies of a given database are page-zeroed in a similar manner.</span></span> <span data-ttu-id="69286-138">Обнуление страницы в активной копии базы данных приводит к обнулению страницы в пассивных копиях базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-138">Zeroing a page on an active database copy causes the page to get zeroed on passive copies of the database.</span></span>

<span data-ttu-id="69286-139">Обнуление страниц записывает двоичный шаблон по сравнению с жестко удаленными записями.</span><span class="sxs-lookup"><span data-stu-id="69286-139">Page zeroing writes a binary pattern over hard-deleted records.</span></span> <span data-ttu-id="69286-140">Шаблон обнуления страниц относится к операциям расширенного обработчика хранилищ (ESE) (имя внутреннего ядра СУБД, используемое серверами в Exchange Online), и оно отличается для операций времени выполнения и фоновых операций обслуживания базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-140">The page-zeroing pattern is specific to Extensible Storage Engine (ESE) operations (the name of the internal database engine used by servers in Exchange Online), and it is different for run-time operations versus background database maintenance operations.</span></span> <span data-ttu-id="69286-141">(Фоновое обслуживание базы данных — это процесс, который непрерывно выполняет проверку контрольных сумм и сканирует каждую базу данных.</span><span class="sxs-lookup"><span data-stu-id="69286-141">(Background database maintenance is a process that continuously checksums and scans each database.</span></span> <span data-ttu-id="69286-142">Основной функцией является контрольная сумма страниц базы данных, но она также обрабатывает очистку пространства и обнуление записей и страниц, которые не были обнулены из-за сбоя хранилища.)</span><span class="sxs-lookup"><span data-stu-id="69286-142">Its primary function is to checksum database pages, but it also handles cleaning up space and zeroing out records and pages that were not zeroed out because of a Store crash.)</span></span>

<span data-ttu-id="69286-143">В следующей таблице перечислены шаблоны заполнения, соответствующие определенным операциям среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="69286-143">The following table lists the fill patterns that correspond to specific run-time operations.</span></span>

| <span data-ttu-id="69286-144">Операция среды выполнения ESE</span><span class="sxs-lookup"><span data-stu-id="69286-144">ESE run-time operation</span></span>   | <span data-ttu-id="69286-145">Шаблон заполнения</span><span class="sxs-lookup"><span data-stu-id="69286-145">Fill pattern</span></span> |
|--------------------------|--------------|
| <span data-ttu-id="69286-146">Заменить</span><span class="sxs-lookup"><span data-stu-id="69286-146">Replace</span></span>                  | <span data-ttu-id="69286-147">R</span><span class="sxs-lookup"><span data-stu-id="69286-147">R</span></span>            |
| <span data-ttu-id="69286-148">Удалить запись или длинное значение</span><span class="sxs-lookup"><span data-stu-id="69286-148">Record/long value delete</span></span> | <span data-ttu-id="69286-149">D</span><span class="sxs-lookup"><span data-stu-id="69286-149">D</span></span>            |
| <span data-ttu-id="69286-150">Освобожденное место страницы</span><span class="sxs-lookup"><span data-stu-id="69286-150">Freed page space</span></span>         | <span data-ttu-id="69286-151">H</span><span class="sxs-lookup"><span data-stu-id="69286-151">H</span></span>            |


<span data-ttu-id="69286-152">В следующей таблице перечислены шаблоны заполнения, соответствующие определенным операциям, выполняемым во время фонового обслуживания базы данных ESE.</span><span class="sxs-lookup"><span data-stu-id="69286-152">The following table lists the fill patterns that correspond to specific operations that occur during ESE background database maintenance.</span></span>

| <span data-ttu-id="69286-153">Операция фонового обслуживания базы данных ESE</span><span class="sxs-lookup"><span data-stu-id="69286-153">ESE background database maintenance operation</span></span> | <span data-ttu-id="69286-154">Шаблон заполнения</span><span class="sxs-lookup"><span data-stu-id="69286-154">Fill pattern</span></span> |
|-----------------------------------------------|--------------|
| <span data-ttu-id="69286-155">Удалить запись</span><span class="sxs-lookup"><span data-stu-id="69286-155">Record delete</span></span>                                 | <span data-ttu-id="69286-156">D</span><span class="sxs-lookup"><span data-stu-id="69286-156">D</span></span>            |
| <span data-ttu-id="69286-157">Удалить длинное значение</span><span class="sxs-lookup"><span data-stu-id="69286-157">Long value delete</span></span>                             | <span data-ttu-id="69286-158">L</span><span class="sxs-lookup"><span data-stu-id="69286-158">L</span></span>            |
| <span data-ttu-id="69286-159">Освобожденное место частично используемой страницы</span><span class="sxs-lookup"><span data-stu-id="69286-159">Freed page space of partially used page</span></span>       | <span data-ttu-id="69286-160">Z</span><span class="sxs-lookup"><span data-stu-id="69286-160">Z</span></span>            |
| <span data-ttu-id="69286-161">Освобожденное место неиспользуемой страницы</span><span class="sxs-lookup"><span data-stu-id="69286-161">Freed page space of unused page</span></span>               | <span data-ttu-id="69286-162">U</span><span class="sxs-lookup"><span data-stu-id="69286-162">U</span></span>            |


### <a name="page-zeroing-process"></a><span data-ttu-id="69286-163">Процесс обнуления страниц</span><span class="sxs-lookup"><span data-stu-id="69286-163">Page Zeroing Process</span></span>
<span data-ttu-id="69286-164">Процесс обнуления страниц зависит от сценария удаления.</span><span class="sxs-lookup"><span data-stu-id="69286-164">The process for page zeroing depends on the deletion scenario.</span></span> <span data-ttu-id="69286-165">В следующей таблице описаны сценарии удаления базы данных и случаи выполнения функций обнуления страниц.</span><span class="sxs-lookup"><span data-stu-id="69286-165">The following table discusses database delete scenarios, and when page zeroing functions occur.</span></span>

| <span data-ttu-id="69286-166">Сценарий удаления базы данных</span><span class="sxs-lookup"><span data-stu-id="69286-166">Database delete scenario</span></span> | <span data-ttu-id="69286-167">Процесс ESE и временные рамки обнуления данных в базе данных</span><span class="sxs-lookup"><span data-stu-id="69286-167">ESE process and timeframe to zero database data</span></span> |
|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="69286-168">Срок хранения элемента истечет на основе срока хранения удаленных элементов.</span><span class="sxs-lookup"><span data-stu-id="69286-168">Item expires based on the deleted item retention period.</span></span> | <span data-ttu-id="69286-169">В асинхронном потоке двоичный шаблон записывается поверх удаленных данных.</span><span class="sxs-lookup"><span data-stu-id="69286-169">An asynchronous thread writes a binary pattern over the deleted data.</span></span> <span data-ttu-id="69286-170">Это действие выполняется за те миллисекунды, в течение которых происходит удаление записи.</span><span class="sxs-lookup"><span data-stu-id="69286-170">This action occurs within milliseconds of the record deletion.</span></span> <span data-ttu-id="69286-171">Если процесс хранилища завершается аварийно, в то время как асинхронно нулевые трудозатраты остаются незавершенными (или очистка хранилища версий отменяется из-за роста хранилища версий), обнуление завершается при выполнении фонового обслуживания базы данных в разделе базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-171">If the Store process crashes while the asynchronous zeroing work is still outstanding (or version store cleanup is canceled due to version store growth), the zeroing is completed when background database maintenance processes that section of the database.</span></span> |
| <span data-ttu-id="69286-172">Сценарий представления: истечение срока действия элементов из Outlook/Outlook в представлении веб-папки (например, представление беседы)</span><span class="sxs-lookup"><span data-stu-id="69286-172">View Scenario: Expiration of items from Outlook/Outlook on the web folder view (for example, Conversation view)</span></span> | <span data-ttu-id="69286-173">Обнуление данных выполняется при обработке этого раздела базы данных во время фонового обслуживания базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-173">Data zeroing occurs when background database maintenance processes that section of the database.</span></span> |
| <span data-ttu-id="69286-174">Сценарий перемещения почтового ящика/удаление почтового ящика: удален исходный почтовый ящик (срок действия удаленного почтового ящика удален)</span><span class="sxs-lookup"><span data-stu-id="69286-174">Move Mailbox/Delete Mailbox Scenario: Source mailbox deleted (expiry of deleted mailbox)</span></span> | <span data-ttu-id="69286-175">Обнуление данных выполняется при обработке этого раздела базы данных во время фонового обслуживания базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-175">Data zeroing occurs when background database maintenance processes that section of the database.</span></span> |

### <a name="mailbox-data-types-without-page-zeroing"></a><span data-ttu-id="69286-176">Типы данных почтового ящика без обнуления страниц</span><span class="sxs-lookup"><span data-stu-id="69286-176">Mailbox Data Types without Page Zeroing</span></span>
<span data-ttu-id="69286-177">Следующие типы данных почтовых ящиков не имеют подположений для обнуления страниц:</span><span class="sxs-lookup"><span data-stu-id="69286-177">The following mailbox data types have no provisions for page zeroing:</span></span>
- <span data-ttu-id="69286-178">**Журналы транзакций базы данных почтовых ящиков** — при удалении журналов транзакций в рамках обычных операций нет процесса для обнуления блоков в файловой системе, в которых хранятся удаленные файлы журналов.</span><span class="sxs-lookup"><span data-stu-id="69286-178">**Mailbox database transaction logs** - When transaction logs are deleted as part of normal operations, there is no process to zero the blocks in the file system that stored the deleted log file(s).</span></span> <span data-ttu-id="69286-179">Скорее всего, файловая система быстро воссоздаст свободное пространство для вновь созданных журналов, но не гарантируется, что это произойдет.</span><span class="sxs-lookup"><span data-stu-id="69286-179">It's likely that the file system will quickly re-utilize that free space for newly created logs, but there is no guarantee that this will happen.</span></span>
- <span data-ttu-id="69286-180">**Файлы каталога индекса контента** — Exchange Online использует для поиска функции индексирования поиска (также называемый быстрым).</span><span class="sxs-lookup"><span data-stu-id="69286-180">**Content index catalog files** - Exchange Online uses Search Foundation (also known as FAST) for search indexing functionality.</span></span> <span data-ttu-id="69286-181">Каталог индексов поиска состоит из нескольких десятков файлов, хранящихся на том же томе, что и файл базы данных почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="69286-181">The search index catalog is composed of several dozen files stored on the same volume as the mailbox database file.</span></span> <span data-ttu-id="69286-182">При необратимом удалении сообщения из базы данных почтовых ящиков связанное с ним содержимое в каталоге поиска не удаляется в тот же момент.</span><span class="sxs-lookup"><span data-stu-id="69286-182">When a message is hard-deleted from the mailbox database, the associated content in the search catalog isn't immediately deleted.</span></span> <span data-ttu-id="69286-183">Удаление контента происходит, когда выполняется теневое (или объединение с главным объединением) нескольких небольших файлов каталога в один большой файл.</span><span class="sxs-lookup"><span data-stu-id="69286-183">Content deletion occurs when Search Foundation does a shadow (or master merge) of many small catalog files in to a single larger file.</span></span> <span data-ttu-id="69286-184">После завершения основного объединения файлы каталога меньшего размера удаляются.</span><span class="sxs-lookup"><span data-stu-id="69286-184">After the master merge completes, the smaller catalog files are deleted.</span></span> <span data-ttu-id="69286-185">Невозможно обнулить блоки, которые хранили удаленные файлы журнала.</span><span class="sxs-lookup"><span data-stu-id="69286-185">There is no process to zero the blocks which stored the deleted catalog files.</span></span>

## <a name="continuous-replication"></a><span data-ttu-id="69286-186">Непрерывная репликация</span><span class="sxs-lookup"><span data-stu-id="69286-186">Continuous Replication</span></span>
<span data-ttu-id="69286-187">Непрерывная репликация (также называемая доставкой журналов и повтором) — технология в Exchange Online, которая создает и поддерживает копии каждой базы данных почтовых ящиков для обеспечения высокой доступности, устойчивости сайтов и аварийного восстановления.</span><span class="sxs-lookup"><span data-stu-id="69286-187">Continuous replication (also known as log shipping and replay) is technology in Exchange Online that creates and maintains copies of every mailbox database to provide high availability, site resilience, and disaster recovery.</span></span> <span data-ttu-id="69286-188">Непрерывная репликация использует поддержку восстановления после сбоя базы данных Exchange Server для предоставления технологии, которая выполняет асинхронное обновление одной или нескольких копий базы данных почтовых ящиков.</span><span class="sxs-lookup"><span data-stu-id="69286-188">Continuous replication leverages the Exchange Server database crash recovery support to provide technology that performs asynchronous updating of one or more copies of a mailbox database.</span></span> <span data-ttu-id="69286-189">Каждый сервер почтовых ящиков записывает обновления баз данных, внесенные в активную базу данных (например, действия электронной почты пользователя), в виде записей журнала в последовательный набор файлов журнала транзакций размером 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="69286-189">Each mailbox server records database updates made on an active database (for example, user email activity) as log records in a sequential set of 1 MB transaction log files.</span></span> <span data-ttu-id="69286-190">Этот набор файлов называется потоком журнала.</span><span class="sxs-lookup"><span data-stu-id="69286-190">This set of files is referred to as the log stream.</span></span> <span data-ttu-id="69286-191">В непрерывной репликации поток журнала также используется для асинхронного обновления одной или нескольких копий базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-191">In continuous replication, the log stream is also used to asynchronously update one or more copies of a database.</span></span> <span data-ttu-id="69286-192">Это достигается путем передачи журналов в расположение, содержащее пассивную копию активной базы данных, а затем воспроизводящее их в пассивную копию базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-192">This is accomplished by transmitting the logs to a location containing a passive copy of the active database and then replaying them into the passive database copy.</span></span> <span data-ttu-id="69286-193">Если все журналы из активной базы данных воспринимаются по пассивной копии базы данных, то эти две базы данных эквивалентны, а все физические изменения, внесенные в активную базу данных, реплицируются на все пассивные копии этой базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-193">If all logs from the active database are replayed against a passive copy of the database, then the two databases are equivalent, and it is through this process that any physical change made to an active database is replicated to all passive copies of that database.</span></span>

<span data-ttu-id="69286-194">Удаление из базы данных почтовых ящиков, независимо от того, является ли элемент почтового ящика или весь почтовый ящик, а также возможность обратимого удаления или жесткое удаление, представляет физическое изменение активной базы данных.</span><span class="sxs-lookup"><span data-stu-id="69286-194">Any deletion from a mailbox database, whether a mailbox item or an entire mailbox, and whether a soft-delete or a hard-delete, represents a physical change to the active database.</span></span> <span data-ttu-id="69286-195">Обнуление страниц также влечет за собой внесение физических изменений в активную базу данных.</span><span class="sxs-lookup"><span data-stu-id="69286-195">Page zeroing also entails making physical changes to the active database.</span></span> <span data-ttu-id="69286-196">Эти изменения записываются в файлы журналов с помощью процесса непрерывной репликации, а при воспроизведении этих файлов журналов для пассивных копий базы данных в эти пассивные базы данных вносятся одни и те же физические изменения.</span><span class="sxs-lookup"><span data-stu-id="69286-196">These changes are written to the log files through a process called continuous replication, and when those log files are replayed against passive copies of the database, the same physical changes are made to those passive databases.</span></span>