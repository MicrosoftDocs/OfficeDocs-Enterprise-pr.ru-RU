---
title: Управление группами Office 365 с помощью PowerShell
ms.author: dianef
author: dianef77
manager: scotv
ms.date: 6/29/2018
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
description: В этой статье пошаговые инструкции для выполнения типичных задач управления для групп в Microsoft PowerShell.
ms.openlocfilehash: 23dfb7f871496b33bf9c34937977b98dc13cea6d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542545"
---
# <a name="manage-office-365-groups-with-powershell"></a>Управление группами Office 365 с помощью PowerShell

 *Последний обновленный 18 апреля 2018 г.* 
  
В этой статье пошаговые инструкции для выполнения типичных задач управления для групп в Microsoft PowerShell. Он также описываются командлеты PowerShell для групп. Сведения об управлении сайтами SharePoint в разделе [Управление SharePoint Online с помощью PowerShell сайтов](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).
  
## <a name="common-tasks-for-managing-office-365-groups"></a>Общие задачи для управления группами Office 365

- [Списки рассылки обновления в Office 365 группы](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f.aspx)
    
- [Управление пользователей, которые можно создавать группы Office 365](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618.aspx)
    
- [Управление доступом гостевой группы Office 365](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96.aspx)
    
- [Управление группами динамически в Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=847632)
    
- Добавление сотни или тысячи пользователей в группы Office 365, используйте [командлет Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a>Ссылка на правила использования вашей группы Office 365
<a name="BK_LinkToGuideLines"> </a>

Когда пользователи [Создание или изменение группы в Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), можно показать их ссылку для вашей организации по его использованию. Например, если требуется специальный префикс или суффикс для добавления имени группы.
  
Используйте Azure Active Directory PowerShell пользователи в вашей организации по его использованию для группы Office 365. Извлечение [командлеты Azure Active Directory для настройки параметров группы](https://go.microsoft.com/fwlink/?LinkID=827484) и выполните действия, описанные в диалоговом окне **создать параметры на уровне папки** для определения гиперссылки рекомендация об использовании. Один раз выполнить командлет AAD, пользователя появится ссылка на требованиями к при их создание или изменение группы в Outlook. 
  
![Создать новую группу со ссылкой на рекомендации по использованию](media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Нажмите кнопку правила использования группы для просмотра вашей организации Office 365 рекомендации по группам](media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a>Разрешить пользователям отправлять как группа Office 365
<a name="BK_LinkToGuideLines"> </a>

Кроме того, это можно сделать в центре администрирования Exchange. В разделе [Разрешить участникам «Отправить как» или «Отправить от имени» группу Office 365](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).
  
Если вы хотите включить группах Office 365 для «Отправить как», используйте командлеты [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) и [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) для настройки этого. После включить этот параметр, для отправки и ответ на электронную почту как группа Office 365 группы пользователей Office 365 можно использовать Outlook или Outlook в Интернете. Пользователи могут перейти в группу, создание новых сообщений электронной почты и измените поле «Отправить как» на адрес электронной почты для группы. 
  
> [!NOTE]
> Необходимо добавить адрес электронной почты группы в поле **«копия»** при создании электронной почты «отправить как», поэтому сообщение отправлено в группу и появляется в групповой беседы. 
  
В настоящее время единственным способом, чтобы обновить политику почтовых ящиков — через [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).
  
- Эта команда используется для установки псевдоним группы.
    
  ```
  $groupAlias = "TestSendAs"
  ```

- Эта команда используется для установки псевдоним пользователя.
    
  ```
  $userAlias = "User"
  ```

- Эта команда используется для передачи groupalias командлет Get-Recipient, чтобы получить сведения о получателе.
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- Выберите имя получателя конечного (имя группы) необходимо передать в командлет Add-RecipientPermission. Псевдоним, для которого будет задано разрешение sendas будет назначен параметр - доверенного объекта.
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- После выполнения командлета, пользователи могут перейти к Outlook или Outlook в Интернете для отправки в виде в группу, добавив адрес электронной почты группы в поле **от** . 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a>Создание классификаций для группы Office в вашей организации

Вы можете создать классификации строк, которые пользователи в вашей организации можно задать при создании группы с Office 365. Например можно разрешить пользователям задавать на группы, которые они создают «Стандартный», «Secret» и «Top Secret». Группа классификации не настроены по умолчанию и вам необходимо создать в пользователи могли установить его. Используйте Windows Azure Active Directory PowerShell пользователи в вашей организации по его использованию для группы Office 365.
  
Извлечение [командлеты Azure Active Directory для настройки параметров группы](https://go.microsoft.com/fwlink/?LinkID=827484) и выполните действия, описанные в диалоговом окне **создать параметры на уровне папки** для определения классификации для группы Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Чтобы связать описание для каждой классификации, которые можно использовать параметры атрибута *ClassificationDescriptions* для определения. 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

Пример.
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

После выполнения командлета выше Azure Active Directory для установки вашей классификации выполните командлет [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) , если вы хотите задать классификации определенной группе. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Или создать новую группу с классификацию.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Ознакомьтесь [С помощью PowerShell с Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) и [подключение к Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) для получения дополнительных сведений об использовании Exchange Online PowerShell. 
  
После включения этих параметров Владелец группы смогут выберите из раскрывающегося меню в Outlook в Outlook и веб-классификация и сохраните его на странице **Изменение** группы. 
  
![Выбор классификации группы Office 365](media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a>Скрытие группы Office 365 из глобального списка адресов
<a name="BKMK_CreateClassification"> </a>

Можно указать, отображается ли группы Office 365 в глобальном списке адресов (GAL) и другие списки в вашей организации. Например при наличии группы юридического отдела, не будет отображаться в списке адресов, можно остановить этой группы будут отображаться в глобальном списке адресов. Запустите командлетов для Set-Unified группы для скрытия группы из списка адресов следующим образом:
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Разрешить внутренним пользователям отправлять сообщения в группу Office 365
<a name="BKMK_CreateClassification"> </a>

Если необходимо запретить пользователям из других организаций для отправки электронной почты в Office 365 группу, можно изменить параметры для этой группы. Он позволяет внутренним пользователям отправлять сообщения электронной почты в группу. При попытке отправить сообщение в эту группу внешних пользователей, они будут отклонены.
  
Запустите командлетов для Set-UnifiedGroup для обновления этого параметра, следующим образом:
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a>Добавлять подсказки группы Office 365
<a name="BKMK_CreateClassification"> </a>

Каждый раз, когда отправитель пытается отправить сообщение электронной почты для группы с Office 365, ему можно будет отображаться подсказки.
  
Запустите командлетов для Set-Unified группы для добавления подсказку для группы:
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

А также подсказка также можно настроить MailTipTranslations, который определяет дополнительные языки для подсказка. Предположим, что необходимо иметь испанский перевод, а затем выполните следующую команду:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a>Изменение отображаемого имени группы Office 365

Отображаемое имя определяет имя группы Office 365. Это имя отображается в exchange admin center или o365 портал администратора. Можно изменить отображаемое имя группы или назначить отображаемое имя для группы Office 365 существующий, выполнив команду Set-UnifiedGroup:
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a>Управление фотографии пользователя в группах Office 365

|**Имя командлета**|**Описание**|
|:-----|:-----|
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Используется для просмотра сведений о фото пользователя, связанные с использованием учетной записи. Фотографии пользователя хранятся в Active Directory  <br/> |
|[SET-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Используется для связи фото пользователя с использованием учетной записи. Фотографии пользователя хранятся в Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Удаление фотографии для группы Office 365  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Измените значение по умолчанию группы Office 365 для Outlook на Public или Private
<a name="BKMK_CreateClassification"> </a>

Office 365 группы в Outlook создаются как частного по умолчанию. Если ваша организация хочет группы Office 365 для Outlook будет создан как Public, по умолчанию (или вернуться к частной), используйте следующий синтаксис командлета PowerShell:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Чтобы задать значение Private:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Чтобы проверить параметр: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Чтобы получить дополнительные сведения, обратитесь к разделу [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) и [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).
  
## <a name="office-365-groups-cmdlets"></a>Командлеты групп Office 365

Следующие командлеты недавно были сделаны доступными в Office 365 группы. Если вы не могут использовать эти, подписки Office 365 не были внесены Данная функциональная возможность еще. Установите флажок центра сообщений и [схема для Office 365](http://roadmap.office.com/en-us).
  
|**Имя командлета**|**Описание**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Этот командлет используется для поиска существующих групп Office 365 и просмотра свойств объекта группы  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Обновление свойств конкретную группу Office 365  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Создание новой группы Office 365. Этот командлет предоставляет минимальный набор параметров, для параметра значения для расширенных свойств используйте Set-UnifiedGroup после создания новой группы  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Удаление существующей группы Office 365  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Получение сведений о членстве и владельца для группы Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Добавление сотни или тысячи пользователей или новых владельцев к существующей группе Office 365  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Удаление владельцы и участники из существующей группы Office 365  <br/> |
   
## <a name="for-more-information"></a>Дополнительные сведения

[Управление Office 365 с помощью PowerShell Office 365](powershell/manage-office-365-with-office-365-powershell.md)
