---
title: Управление группами Office 365 с помощью PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Узнайте, как для выполнения типичных задач управления для Office 365 групп в Microsoft PowerShell.
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760061"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="4c079-103">Управление группами Office 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c079-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="4c079-104">*Последний обновленный 18 апреля 2018 г.*</span><span class="sxs-lookup"><span data-stu-id="4c079-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="4c079-p101">В этой статье пошаговые инструкции для выполнения типичных задач управления для групп в Microsoft PowerShell. Он также описываются командлеты PowerShell для групп. Сведения об управлении сайтами SharePoint в разделе [Управление SharePoint Online с помощью PowerShell сайтов](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="4c079-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="4c079-108">Ссылка на правила использования вашей группы Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="4c079-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="4c079-109"></span></span>

<span data-ttu-id="4c079-p102">Когда пользователи [Создание или изменение группы в Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), можно показать их ссылку для вашей организации по его использованию. Например, если требуется специальный префикс или суффикс для добавления имени группы.</span><span class="sxs-lookup"><span data-stu-id="4c079-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="4c079-p103">Используйте Azure Active Directory PowerShell пользователи в вашей организации по его использованию для группы Office 365. Извлечение [командлеты Azure Active Directory для настройки параметров группы](https://go.microsoft.com/fwlink/?LinkID=827484) и выполните действия, описанные в диалоговом окне **создать параметры на уровне папки** для определения гиперссылки рекомендация об использовании. Один раз выполнить командлет AAD, пользователя появится ссылка на требованиями к при их создание или изменение группы в Outlook.</span><span class="sxs-lookup"><span data-stu-id="4c079-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Создать новую группу со ссылкой на рекомендации по использованию](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Нажмите кнопку правила использования группы для просмотра вашей организации Office 365 рекомендации по группам](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="4c079-117">Разрешить пользователям отправлять как группа Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="4c079-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="4c079-118"></span></span>
  
<span data-ttu-id="4c079-p104">Если вы хотите включить группах Office 365 для «Отправить как», используйте командлеты [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) и [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) для настройки этого. После включить этот параметр, для отправки и ответ на электронную почту как группа Office 365 группы пользователей Office 365 можно использовать Outlook или Outlook в Интернете. Пользователи могут перейти в группу, создание новых сообщений электронной почты и измените поле «Отправить как» на адрес электронной почты для группы.</span><span class="sxs-lookup"><span data-stu-id="4c079-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="4c079-122">([Также это возможно в центре администрирования Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="4c079-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="4c079-p105">Используйте следующий сценарий, заменив \* \<GroupAlias\> \* с псевдонимом группы, которую требуется обновить, и \* \<псевдоним\> \* с псевдоним пользователя, которому вы хотите предоставить прав. [Подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) для запуска этого сценария.</span><span class="sxs-lookup"><span data-stu-id="4c079-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="4c079-125">После выполнения командлета, пользователи могут перейти к Outlook или Outlook в Интернете для отправки в виде в группу, добавив адрес электронной почты группы в поле **от** .</span><span class="sxs-lookup"><span data-stu-id="4c079-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="4c079-126">Создание классификаций для группы Office в вашей организации</span><span class="sxs-lookup"><span data-stu-id="4c079-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="4c079-p106">Вы можете создать классификации строк, которые пользователи в вашей организации можно задать при создании группы с Office 365. Например можно разрешить пользователям задавать на группы, которые они создают «Стандартный», «Secret» и «Top Secret». Группа классификации не настроены по умолчанию и вам необходимо создать в пользователи могли установить его. Используйте Windows Azure Active Directory PowerShell пользователи в вашей организации по его использованию для группы Office 365.</span><span class="sxs-lookup"><span data-stu-id="4c079-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="4c079-131">Извлечение [командлеты Azure Active Directory для настройки параметров группы](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) и выполните действия, описанные в диалоговом окне **создать параметры на уровне папки** для определения классификации для группы Office 365.</span><span class="sxs-lookup"><span data-stu-id="4c079-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="4c079-132">Чтобы связать описание для каждой классификации, которые можно использовать параметры атрибута *ClassificationDescriptions* для определения.</span><span class="sxs-lookup"><span data-stu-id="4c079-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="4c079-133">где классификации сопоставляет строки в ClassificationList.</span><span class="sxs-lookup"><span data-stu-id="4c079-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="4c079-134">Пример.</span><span class="sxs-lookup"><span data-stu-id="4c079-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="4c079-135">После выполнения командлета выше Azure Active Directory для установки вашей классификации выполните командлет [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) , если вы хотите задать классификации определенной группе.</span><span class="sxs-lookup"><span data-stu-id="4c079-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="4c079-136">Или создать новую группу с классификацию.</span><span class="sxs-lookup"><span data-stu-id="4c079-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="4c079-137">Сведения об использовании Exchange Online PowerShell см. в статьях [Использование PowerShell с Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) и [Подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="4c079-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="4c079-138">После включения этих параметров Владелец группы смогут выберите из раскрывающегося меню в Outlook в Outlook и веб-классификация и сохраните его на странице **Изменение** группы.</span><span class="sxs-lookup"><span data-stu-id="4c079-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Выбор классификации группы Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="4c079-140">Скрытие группы Office 365 из глобального списка адресов</span><span class="sxs-lookup"><span data-stu-id="4c079-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="4c079-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="4c079-141"></span></span>

<span data-ttu-id="4c079-p107">Можно указать, отображается ли группы Office 365 в глобальном списке адресов (GAL) и другие списки в вашей организации. Например при наличии группы юридического отдела, не будет отображаться в списке адресов, можно остановить этой группы будут отображаться в глобальном списке адресов. Выполните командлет Set-Unified группы, чтобы скрыть группу из списка адресов следующим образом:</span><span class="sxs-lookup"><span data-stu-id="4c079-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="4c079-145">Разрешить внутренним пользователям отправлять сообщения в группу Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="4c079-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="4c079-146"></span></span>

<span data-ttu-id="4c079-p108">Если необходимо запретить пользователям из других организаций для отправки электронной почты в Office 365 группу, можно изменить параметры для этой группы. Он позволяет внутренним пользователям отправлять сообщения электронной почты в группу. При попытке отправить сообщение в эту группу внешних пользователей, они будут отклонены.</span><span class="sxs-lookup"><span data-stu-id="4c079-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="4c079-150">Выполните командлет Set-UnifiedGroup для обновления этого параметра, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="4c079-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="4c079-151">Добавлять подсказки группы Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="4c079-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="4c079-152"></span></span>

<span data-ttu-id="4c079-153">Каждый раз, когда отправитель пытается отправить сообщение электронной почты для группы с Office 365, к ним могут отображаться подсказки.</span><span class="sxs-lookup"><span data-stu-id="4c079-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="4c079-154">Выполните командлет Set-Unified группы, чтобы добавить подсказку для группы:</span><span class="sxs-lookup"><span data-stu-id="4c079-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="4c079-p109">А также подсказка также можно настроить MailTipTranslations, который определяет дополнительные языки для подсказка. Предположим, что необходимо иметь испанский перевод, а затем выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="4c079-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="4c079-157">Изменение отображаемого имени группы Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="4c079-p110">Отображаемое имя определяет имя группы Office 365. Можно просмотреть это имя в центре администрирования exchange или портала администрирования Office 365. Можно изменить отображаемое имя группы или назначить отображаемое имя существующей группы Office 365 с помощью команды Set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="4c079-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="4c079-161">Измените значение по умолчанию группы Office 365 для Outlook на Public или Private</span><span class="sxs-lookup"><span data-stu-id="4c079-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="4c079-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="4c079-162"></span></span>

<span data-ttu-id="4c079-p111">Office 365 группы в Outlook создаются как частного по умолчанию. Если ваша организация хочет группы Office 365 будет создан как Public, по умолчанию (или вернуться к частной), используйте следующий синтаксис командлета PowerShell:</span><span class="sxs-lookup"><span data-stu-id="4c079-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="4c079-165">Чтобы задать значение Private:</span><span class="sxs-lookup"><span data-stu-id="4c079-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="4c079-166">Чтобы проверить параметр:</span><span class="sxs-lookup"><span data-stu-id="4c079-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="4c079-167">Чтобы получить дополнительные сведения, обратитесь к разделу [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) и [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="4c079-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="4c079-168">Командлеты групп Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="4c079-169">С помощью Office 365 группы можно использовать следующие командлеты.</span><span class="sxs-lookup"><span data-stu-id="4c079-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="4c079-170">**Имя командлета**</span><span class="sxs-lookup"><span data-stu-id="4c079-170">**Cmdlet name**</span></span>|<span data-ttu-id="4c079-171">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c079-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="4c079-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="4c079-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="4c079-173">Этот командлет используется для поиска существующих групп Office 365 и просмотра свойств объекта группы</span><span class="sxs-lookup"><span data-stu-id="4c079-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="4c079-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="4c079-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="4c079-175">Обновление свойств конкретную группу Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4c079-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="4c079-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="4c079-p112">Создание новой группы Office 365. Этот командлет предоставляет минимальный набор параметров, для параметра значения для расширенных свойств используйте Set-UnifiedGroup после создания новой группы</span><span class="sxs-lookup"><span data-stu-id="4c079-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="4c079-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="4c079-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="4c079-180">Удаление существующей группы Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4c079-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="4c079-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="4c079-182">Получение сведений о членстве и владельца для группы Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4c079-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="4c079-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="4c079-184">Добавление сотни или тысячи пользователей или новых владельцев к существующей группе Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4c079-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="4c079-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="4c079-186">Удаление владельцы и участники из существующей группы Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4c079-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="4c079-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="4c079-p113">Используется для просмотра сведений о фото пользователя, связанные с использованием учетной записи. Фотографии пользователя хранятся в Active Directory</span><span class="sxs-lookup"><span data-stu-id="4c079-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="4c079-190">SET-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="4c079-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="4c079-p114">Используется для связи фото пользователя с использованием учетной записи. Фотографии пользователя хранятся в Active Directory</span><span class="sxs-lookup"><span data-stu-id="4c079-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="4c079-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="4c079-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="4c079-194">Удаление фотографии для группы Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="4c079-195">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="4c079-195">Related topics</span></span>

[<span data-ttu-id="4c079-196">Списки рассылки обновления в Office 365 группы</span><span class="sxs-lookup"><span data-stu-id="4c079-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="4c079-197">Управление разрешениями пользователей на создание групп Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="4c079-198">Управление гостевым доступом к Группам Office 365</span><span class="sxs-lookup"><span data-stu-id="4c079-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="4c079-199">Изменение членства в группе статического для динамического в</span><span class="sxs-lookup"><span data-stu-id="4c079-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
