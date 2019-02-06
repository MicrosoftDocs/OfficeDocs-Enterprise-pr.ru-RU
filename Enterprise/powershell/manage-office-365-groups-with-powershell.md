---
title: Управление группами Office 365 с помощью PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Последний обновленный 18 апреля 2018 г.
ms.openlocfilehash: 518f845099a72d9addac13388d1b281ca63ee408
ms.sourcegitcommit: e56f830ccff8d74d9edbff4a46a9ee1d613291ed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2019
ms.locfileid: "29741222"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="dd6e4-103">Управление группами Office 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd6e4-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="dd6e4-104">*Последний обновленный 18 апреля 2018 г.*</span><span class="sxs-lookup"><span data-stu-id="dd6e4-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="dd6e4-p101">В этой статье пошаговые инструкции для выполнения типичных задач управления для групп в Microsoft PowerShell. Он также описываются командлеты PowerShell для групп. Сведения об управлении сайтами SharePoint в разделе [Управление веб-сайтов групп и сайты обмена данными с помощью PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage team sites and communication sites by using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="dd6e4-108">Общие задачи для управления группами Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="dd6e4-109">Обновление списков рассылки до групп Office 365 в Outlook</span><span class="sxs-lookup"><span data-stu-id="dd6e4-109">Upgrade distribution lists to Office 365 Groups in Outlook</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [<span data-ttu-id="dd6e4-110">Управление разрешениями пользователей на создание групп Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [<span data-ttu-id="dd6e4-111">Управление гостевым доступом к Группам Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [<span data-ttu-id="dd6e4-112">Управление группами динамически в Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="dd6e4-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="dd6e4-113">Добавление сотни или тысячи пользователей в группы Office 365, используйте [командлет Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span><span class="sxs-lookup"><span data-stu-id="dd6e4-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="dd6e4-114">Ссылка на правила использования вашей группы Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="dd6e4-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-115"></span></span>

<span data-ttu-id="dd6e4-p102">Когда пользователи [Создать группу в Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), можно показать их ссылку для вашей организации по его использованию. Например, если требуется специальный префикс или суффикс для добавления имени группы.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p102">When users [Create a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="dd6e4-p103">Используйте Azure Active Directory PowerShell пользователи в вашей организации по его использованию для группы Office 365. Извлечение [командлеты Azure Active Directory для настройки параметров группы](https://go.microsoft.com/fwlink/?LinkID=827484) и выполните действия, описанные в диалоговом окне **создать параметры на уровне папки** для определения гиперссылки рекомендация об использовании. Один раз выполнить командлет AAD, пользователя появится ссылка на требованиями к при их создание или изменение группы в Outlook.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Создать новую группу со ссылкой на рекомендации по использованию](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Нажмите кнопку правила использования группы для просмотра вашей организации Office 365 рекомендации по группам](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="dd6e4-123">Разрешить пользователям отправлять как группа Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="dd6e4-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-124"></span></span>

<span data-ttu-id="dd6e4-p104">Кроме того, это можно сделать в центре администрирования Exchange. В разделе [Разрешить участникам отправлять в виде или отправлять сообщения от имени группы](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p104">You can also do this in the Exchange Admin Center. See [Allow members to send as or send on behalf of a Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).</span></span>
  
<span data-ttu-id="dd6e4-p105">Если вы хотите включить группах Office 365 для «Отправить как», используйте командлеты [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) и [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) для настройки этого. После включить этот параметр, для отправки и ответ на электронную почту как группа Office 365 группы пользователей Office 365 можно использовать Outlook или Outlook в Интернете. Пользователи могут перейти в группу, создание новых сообщений электронной почты и измените поле «Отправить как» на адрес электронной почты для группы.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="dd6e4-130">Необходимо добавить адрес электронной почты группы в поле **«копия»** при создании электронной почты «отправить как», поэтому сообщение отправлено в группу и появляется в групповой беседы.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="dd6e4-131">В настоящее время единственным способом, чтобы обновить политику почтовых ящиков — через [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span><span class="sxs-lookup"><span data-stu-id="dd6e4-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="dd6e4-132">Эта команда используется для установки псевдоним группы.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="dd6e4-133">Эта команда используется для установки псевдоним пользователя.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="dd6e4-134">Эта команда используется для передачи groupalias командлет Get-Recipient, чтобы получить сведения о получателе.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="dd6e4-p106">Выберите имя получателя конечного (имя группы) необходимо передать в командлет Add-RecipientPermission. Псевдоним, для которого будет задано разрешение sendas будет назначен параметр - доверенного объекта.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="dd6e4-137">После выполнения командлета, пользователи могут перейти к Outlook или Outlook в Интернете для отправки в виде в группу, добавив адрес электронной почты группы в поле **от** .</span><span class="sxs-lookup"><span data-stu-id="dd6e4-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="dd6e4-138">Создание классификаций для группы Office в вашей организации</span><span class="sxs-lookup"><span data-stu-id="dd6e4-138">Create classifications for Office groups in your organization</span></span>
<span data-ttu-id="dd6e4-139"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-139"></span></span>

<span data-ttu-id="dd6e4-p107">Вы можете создать классификации строк, которые пользователи в вашей организации можно задать при создании группы с Office 365. Например можно разрешить пользователям задавать на группы, которые они создают «Стандартный», «Secret» и «Top Secret». Группа классификации не настроены по умолчанию и вам необходимо создать в пользователи могли установить его. Используйте Windows Azure Active Directory PowerShell пользователи в вашей организации по его использованию для группы Office 365.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="dd6e4-144">Извлечение [командлеты Azure Active Directory для настройки параметров группы](https://go.microsoft.com/fwlink/?LinkID=827484) и выполните действия, описанные в диалоговом окне **создать параметры на уровне папки** для определения классификации для группы Office 365.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-144">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="dd6e4-145">Чтобы связать описание для каждой классификации, которые можно использовать параметры атрибута *ClassificationDescriptions* для определения.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-145">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="dd6e4-146">Пример:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-146">For example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="dd6e4-147">После выполнения командлета выше Azure Active Directory для установки вашей классификации выполните командлет [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) , если вы хотите задать классификации определенной группе.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-147">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="dd6e4-148">Или создать новую группу с классификацию.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-148">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="dd6e4-149">Сведения об использовании Exchange Online PowerShell см. в статьях [Использование PowerShell с Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) и [Подключение к Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415).</span><span class="sxs-lookup"><span data-stu-id="dd6e4-149">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="dd6e4-150">После включения этих параметров Владелец группы смогут выберите из раскрывающегося меню в Outlook в Outlook и веб-классификация и сохраните его на странице **Изменение** группы.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-150">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Выбор классификации группы Office 365](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="dd6e4-152">Скрытие группы Office 365 из глобального списка адресов</span><span class="sxs-lookup"><span data-stu-id="dd6e4-152">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="dd6e4-153"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-153"></span></span>

<span data-ttu-id="dd6e4-p108">Можно указать, отображается ли группы Office 365 в глобальном списке адресов (GAL) и другие списки в вашей организации. Например при наличии группы юридического отдела, не будет отображаться в списке адресов, можно остановить этой группы будут отображаться в глобальном списке адресов. Запустите командлетов для Set-Unified группы для скрытия группы из списка адресов следующим образом:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="dd6e4-157">Разрешить внутренним пользователям отправлять сообщения в группу Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-157">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="dd6e4-158"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-158"></span></span>

<span data-ttu-id="dd6e4-p109">Если необходимо запретить пользователям из других организаций для отправки электронной почты в Office 365 группу, можно изменить параметры для этой группы. Он позволяет внутренним пользователям отправлять сообщения электронной почты в группу. При попытке отправить сообщение в эту группу внешних пользователей, они будут отклонены.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="dd6e4-162">Запустите командлетов для Set-UnifiedGroup для обновления этого параметра, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-162">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="dd6e4-163">Добавлять подсказки группы Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-163">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="dd6e4-164"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-164"></span></span>

<span data-ttu-id="dd6e4-165">Каждый раз, когда отправитель пытается отправить сообщение электронной почты для группы с Office 365, ему можно будет отображаться подсказки.</span><span class="sxs-lookup"><span data-stu-id="dd6e4-165">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="dd6e4-166">Запустите командлетов для Set-Unified группы для добавления подсказку для группы:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-166">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="dd6e4-p110">А также подсказка также можно настроить MailTipTranslations, который определяет дополнительные языки для подсказка. Предположим, что необходимо иметь испанский перевод, а затем выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="dd6e4-169">Изменение отображаемого имени группы Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-169">Change Display name of the Office 365 group</span></span>
<span data-ttu-id="dd6e4-170"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-170"></span></span>

<span data-ttu-id="dd6e4-p111">Отображаемое имя определяет имя группы Office 365. Это имя отображается в exchange admin center или o365 портал администратора. Можно изменить отображаемое имя группы или назначить отображаемое имя для группы Office 365 существующий, выполнив команду Set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="dd6e4-174">Управление фотографии пользователя в группах Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-174">Manage user photos in Office 365 Groups</span></span>
<span data-ttu-id="dd6e4-175"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-175"></span></span>

<span data-ttu-id="dd6e4-176">| |</span><span class="sxs-lookup"><span data-stu-id="dd6e4-176"></span></span>
|<span data-ttu-id="dd6e4-177">**Имя командлета**</span><span class="sxs-lookup"><span data-stu-id="dd6e4-177">**Cmdlet name**</span></span>|<span data-ttu-id="dd6e4-178">**Описание**</span><span class="sxs-lookup"><span data-stu-id="dd6e4-178">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="dd6e4-179">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="dd6e4-179">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="dd6e4-p112">Используется для просмотра сведений о фото пользователя, связанные с использованием учетной записи. Фотографии пользователя хранятся в Active Directory</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="dd6e4-182">SET-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="dd6e4-182">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="dd6e4-p113">Используется для связи фото пользователя с использованием учетной записи. Фотографии пользователя хранятся в Active Directory</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="dd6e4-185">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="dd6e4-185">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="dd6e4-186">Удаление фотографии для группы Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-186">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="dd6e4-187">Измените значение по умолчанию группы Office 365 для Outlook на Public или Private</span><span class="sxs-lookup"><span data-stu-id="dd6e4-187">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="dd6e4-188"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="dd6e4-188"></span></span>

<span data-ttu-id="dd6e4-p114">Office 365 группы в Outlook создаются как частного по умолчанию. Если ваша организация хочет группы Office 365 для Outlook будет создан как Public, по умолчанию (или вернуться к частной), используйте следующий синтаксис командлета PowerShell:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="dd6e4-191">Чтобы задать значение Private:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-191">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="dd6e4-192">Чтобы проверить параметр:</span><span class="sxs-lookup"><span data-stu-id="dd6e4-192">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="dd6e4-193">Чтобы получить дополнительные сведения, обратитесь к разделу [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) и [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span><span class="sxs-lookup"><span data-stu-id="dd6e4-193">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="dd6e4-194">Командлеты групп Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-194">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="dd6e4-p115">Следующие командлеты недавно были сделаны доступными в Office 365 группы. Если вы не могут использовать эти, подписки Office 365 не были внесены Данная функциональная возможность еще. Установите флажок центра сообщений и [схема для Office 365](http://roadmap.office.com/en-us).</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Office 365 Roadmap](http://roadmap.office.com/en-us).</span></span>
  
<span data-ttu-id="dd6e4-198">| |</span><span class="sxs-lookup"><span data-stu-id="dd6e4-198"></span></span>
|<span data-ttu-id="dd6e4-199">**Имя командлета**</span><span class="sxs-lookup"><span data-stu-id="dd6e4-199">**Cmdlet name**</span></span>|<span data-ttu-id="dd6e4-200">**Описание**</span><span class="sxs-lookup"><span data-stu-id="dd6e4-200">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="dd6e4-201">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="dd6e4-201">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="dd6e4-202">Этот командлет используется для поиска существующих групп Office 365 и просмотра свойств объекта группы</span><span class="sxs-lookup"><span data-stu-id="dd6e4-202">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="dd6e4-203">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="dd6e4-203">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="dd6e4-204">Обновление свойств конкретную группу Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-204">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="dd6e4-205">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="dd6e4-205">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="dd6e4-p116">Создание новой группы Office 365. Этот командлет предоставляет минимальный набор параметров, для параметра значения для расширенных свойств используйте Set-UnifiedGroup после создания новой группы</span><span class="sxs-lookup"><span data-stu-id="dd6e4-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="dd6e4-208">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="dd6e4-208">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="dd6e4-209">Удаление существующей группы Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-209">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="dd6e4-210">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="dd6e4-210">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="dd6e4-211">Получение сведений о членстве и владельца для группы Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-211">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="dd6e4-212">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="dd6e4-212">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="dd6e4-213">Добавление сотни или тысячи пользователей или новых владельцев к существующей группе Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-213">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="dd6e4-214">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="dd6e4-214">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="dd6e4-215">Удаление владельцы и участники из существующей группы Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-215">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="dd6e4-216">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="dd6e4-216">For more information</span></span>

- [<span data-ttu-id="dd6e4-217">С помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd6e4-217">Using PowerShell</span></span>](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [<span data-ttu-id="dd6e4-218">Применение или удаление политики почтовых ящиков Outlook Web App в почтовом ящике</span><span class="sxs-lookup"><span data-stu-id="dd6e4-218">Apply or remove an Outlook Web App mailbox policy on a mailbox</span></span>](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="dd6e4-219">Политику именования групп с Office 365</span><span class="sxs-lookup"><span data-stu-id="dd6e4-219">Office 365 Groups naming policy</span></span>](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

