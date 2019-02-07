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
# <a name="manage-office-365-groups-with-powershell"></a>Управление группами Office 365 с помощью PowerShell

 *Последний обновленный 18 апреля 2018 г.* 
  
В этой статье пошаговые инструкции для выполнения типичных задач управления для групп в Microsoft PowerShell. Он также описываются командлеты PowerShell для групп. Сведения об управлении сайтами SharePoint в разделе [Управление SharePoint Online с помощью PowerShell сайтов](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Ссылка на правила использования вашей группы Office 365
<a name="BK_LinkToGuideLines"> </a>

Когда пользователи [Создание или изменение группы в Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), можно показать их ссылку для вашей организации по его использованию. Например, если требуется специальный префикс или суффикс для добавления имени группы.
  
Используйте Azure Active Directory PowerShell пользователи в вашей организации по его использованию для группы Office 365. Извлечение [командлеты Azure Active Directory для настройки параметров группы](https://go.microsoft.com/fwlink/?LinkID=827484) и выполните действия, описанные в диалоговом окне **создать параметры на уровне папки** для определения гиперссылки рекомендация об использовании. Один раз выполнить командлет AAD, пользователя появится ссылка на требованиями к при их создание или изменение группы в Outlook. 
  
![Создать новую группу со ссылкой на рекомендации по использованию](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Нажмите кнопку правила использования группы для просмотра вашей организации Office 365 рекомендации по группам](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>Разрешить пользователям отправлять как группа Office 365
<a name="BK_LinkToGuideLines"> </a>
  
Если вы хотите включить группах Office 365 для «Отправить как», используйте командлеты [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) и [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) для настройки этого. После включить этот параметр, для отправки и ответ на электронную почту как группа Office 365 группы пользователей Office 365 можно использовать Outlook или Outlook в Интернете. Пользователи могут перейти в группу, создание новых сообщений электронной почты и измените поле «Отправить как» на адрес электронной почты для группы. 

([Также это возможно в центре администрирования Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).
  
Используйте следующий сценарий, заменив * \<GroupAlias\> * с псевдонимом группы, которую требуется обновить, и * \<псевдоним\> * с псевдоним пользователя, которому вы хотите предоставить прав. [Подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) для запуска этого сценария.

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

После выполнения командлета, пользователи могут перейти к Outlook или Outlook в Интернете для отправки в виде в группу, добавив адрес электронной почты группы в поле **от** . 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>Создание классификаций для группы Office в вашей организации

Вы можете создать классификации строк, которые пользователи в вашей организации можно задать при создании группы с Office 365. Например можно разрешить пользователям задавать на группы, которые они создают «Стандартный», «Secret» и «Top Secret». Группа классификации не настроены по умолчанию и вам необходимо создать в пользователи могли установить его. Используйте Windows Azure Active Directory PowerShell пользователи в вашей организации по его использованию для группы Office 365.
  
Извлечение [командлеты Azure Active Directory для настройки параметров группы](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) и выполните действия, описанные в диалоговом окне **создать параметры на уровне папки** для определения классификации для группы Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Чтобы связать описание для каждой классификации, которые можно использовать параметры атрибута *ClassificationDescriptions* для определения.
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

где классификации сопоставляет строки в ClassificationList.

Пример.
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

После выполнения командлета выше Azure Active Directory для установки вашей классификации выполните командлет [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) , если вы хотите задать классификации определенной группе. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Или создать новую группу с классификацию.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Сведения об использовании Exchange Online PowerShell см. в статьях [Использование PowerShell с Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) и [Подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 
  
После включения этих параметров Владелец группы смогут выберите из раскрывающегося меню в Outlook в Outlook и веб-классификация и сохраните его на странице **Изменение** группы. 
  
![Выбор классификации группы Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>Скрытие группы Office 365 из глобального списка адресов
<a name="BKMK_CreateClassification"> </a>

Можно указать, отображается ли группы Office 365 в глобальном списке адресов (GAL) и другие списки в вашей организации. Например при наличии группы юридического отдела, не будет отображаться в списке адресов, можно остановить этой группы будут отображаться в глобальном списке адресов. Выполните командлет Set-Unified группы, чтобы скрыть группу из списка адресов следующим образом:
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Разрешить внутренним пользователям отправлять сообщения в группу Office 365
<a name="BKMK_CreateClassification"> </a>

Если необходимо запретить пользователям из других организаций для отправки электронной почты в Office 365 группу, можно изменить параметры для этой группы. Он позволяет внутренним пользователям отправлять сообщения электронной почты в группу. При попытке отправить сообщение в эту группу внешних пользователей, они будут отклонены.
  
Выполните командлет Set-UnifiedGroup для обновления этого параметра, следующим образом:

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>Добавлять подсказки группы Office 365
<a name="BKMK_CreateClassification"> </a>

Каждый раз, когда отправитель пытается отправить сообщение электронной почты для группы с Office 365, к ним могут отображаться подсказки.
  
Выполните командлет Set-Unified группы, чтобы добавить подсказку для группы:

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

А также подсказка также можно настроить MailTipTranslations, который определяет дополнительные языки для подсказка. Предположим, что необходимо иметь испанский перевод, а затем выполните следующую команду:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Изменение отображаемого имени группы Office 365

Отображаемое имя определяет имя группы Office 365. Можно просмотреть это имя в центре администрирования exchange или портала администрирования Office 365. Можно изменить отображаемое имя группы или назначить отображаемое имя существующей группы Office 365 с помощью команды Set-UnifiedGroup:

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Измените значение по умолчанию группы Office 365 для Outlook на Public или Private
<a name="BKMK_CreateClassification"> </a>

Office 365 группы в Outlook создаются как частного по умолчанию. Если ваша организация хочет группы Office 365 будет создан как Public, по умолчанию (или вернуться к частной), используйте следующий синтаксис командлета PowerShell:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Чтобы задать значение Private:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Чтобы проверить параметр: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Чтобы получить дополнительные сведения, обратитесь к разделу [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) и [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).
  
## <a name="office-365-groups-cmdlets"></a>Командлеты групп Office 365

С помощью Office 365 группы можно использовать следующие командлеты.
  
|**Имя командлета**|**Описание**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Этот командлет используется для поиска существующих групп Office 365 и просмотра свойств объекта группы  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Обновление свойств конкретную группу Office 365  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Создание новой группы Office 365. Этот командлет предоставляет минимальный набор параметров, для параметра значения для расширенных свойств используйте Set-UnifiedGroup после создания новой группы  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Удаление существующей группы Office 365  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Получение сведений о членстве и владельца для группы Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Добавление сотни или тысячи пользователей или новых владельцев к существующей группе Office 365  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Удаление владельцы и участники из существующей группы Office 365  <br/> |
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Используется для просмотра сведений о фото пользователя, связанные с использованием учетной записи. Фотографии пользователя хранятся в Active Directory  <br/> |
|[SET-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Используется для связи фото пользователя с использованием учетной записи. Фотографии пользователя хранятся в Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Удаление фотографии для группы Office 365  <br/> |

## <a name="related-topics"></a>Статьи по теме

[Списки рассылки обновления в Office 365 группы](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[Управление разрешениями пользователей на создание групп Office 365](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[Управление гостевым доступом к Группам Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Изменение членства в группе статического для динамического в](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
