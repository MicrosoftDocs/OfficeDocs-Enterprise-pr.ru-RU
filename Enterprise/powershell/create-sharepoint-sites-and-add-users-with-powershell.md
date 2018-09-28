---
title: Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Сводка: Использование PowerShell Office 365 для создания новых сайтов SharePoint Online, а затем добавьте пользователей и групп для этих сайтов.'
ms.openlocfilehash: 41ca26249bd494d5603a425689e47f9fe6809f1a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975207"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell

 **Сводка:** Для создания новых сайтов SharePoint Online с помощью Office 365 PowerShell, а затем добавьте пользователей и групп для этих сайтов.

При использовании Office 365 PowerShell для создания сайтов SharePoint Online и добавление пользователей можно быстро и повторно выполнить задачи значительно быстрее, чем в центре администрирования Office 356. Можно также выполнять задачи, которые невозможно выполнить в центре администрирования Office 356. 

## <a name="before-you-begin"></a>Перед началом работы

Процедуры, описанные в этом разделе требуется подключение к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Шаг 1. Создание семейств веб-сайтов с помощью Office 365 PowerShell

Создайте несколько сайтов с помощью Office 365 PowerShell и CSV-файла. Чтобы создать CSV-файл, используйте пример кода и "Блокнот". Для этого необходимо заменить содержимое заполнителей в угловых скобках на данные о сайтах и клиенте. Эта процедура позволяет создать один файл и выполнить одну команду Office 365 PowerShell, которая использует этот файл. Благодаря этому действия можно повторять в разных средах, а также устраняются многие, если не все, ошибки, связанные с вводом длинных команд в командной консоли SharePoint Online. Эта процедура состоит из двух частей. Сначала вы создаете CSV-файл, а затем ссылаетесь на него с помощью Office 365 PowerShell. Содержимое файла будет использоваться для создания сайтов.

Командлет Office 365 PowerShell импортирует CSV-файл и передает его в цикл в фигурных скобках, который считывает первую строку файла как заголовки столбцов. Командлет Office 365 PowerShell проходит по остальным записям, создает семейство веб-сайтов для каждой из них и назначает свойства семейства веб-сайтов в соответствии с заголовками столбцов.

### <a name="create-a-csv-file"></a>Создание CSV-файла

1. Откройте Блокнот и вставьте в него следующий блок текста:<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>Где *клиента* — это имя клиента, а *владелец* — это имя пользователя в клиенте, которому необходимо предоставить роль основного администратора семейства сайтов.<br/>(Клавиши Ctrl + H может, при использовании "Блокнот" для массового заменить быстрее.)<br/>

2. Сохраните файл на рабочем столе как **SiteCollections.csv**.<br/>

> [!TIP]
> Прежде чем использовать это или любой другой .csv или файл сценария Windows PowerShell, рекомендуется убедитесь в том, что не используются никакие лишние или непечатаемые символы. Откройте файл Word и на ленте, щелкните значок абзаца, чтобы показать непечатаемые символы. Должно быть не лишние непечатаемых знаков. Например должно быть не служебные знаки за последний один в конце файла.

### <a name="run-the-windows-powershell-command"></a>Выполнение команды Windows PowerShell

1. В командной строке Windows PowerShell введите или скопируйте и вставьте следующий командлет, а затем нажмите клавишу ВВОД:<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>Где *MyAlias* — это псевдоним пользователя.<br/>

2. Дождитесь появления окна командной строки Windows PowerShell. Для этого может потребоваться одна или две минуты.<br/>

3. В командной строке Windows PowerShell введите или скопируйте и вставьте следующий командлет, а затем нажмите клавишу ВВОД:<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. Обратите внимание, новых семейств сайтов в списке. Должно появиться следующие семейства сайтов: **сайтов contosotest**, **TeamSite01**, **Blog01**и **Project01**

Вот и все. Вы создали несколько семейств веб-сайтов с помощью CSV-файла и одного командлета Windows PowerShell. Теперь вы можете создать пользователей и назначить их сайтам.

## <a name="step-2-add-users-and-groups"></a>Действие 2. Добавление пользователей или групп

Теперь мы создадим пользователей и добавим их в группу семейства сайтов. Мы используем CSV-файл для массовой загрузки новых групп и пользователей.

В следующих процедурах предполагается, что вы успешно создали семейства сайтов contosotest, TeamSite01, Blog01 и Project01.

### <a name="create-csv-and-ps1-files"></a>Создание CSV- и PS1-файлов

1. Откройте Блокнот и вставьте в него следующий блок текста:<br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>Где *клиента* — это имя клиента.<br/>

2. Сохраните файл на рабочем столе как **GroupsAndPermissions.csv**.<br/>

3. Откройте новый экземпляр Блокнота и вставьте в него следующий блок текста:<br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>Где *клиента* — это имя клиента, а *имя пользователя* — имя существующего пользователя.<br/>

4. Сохраните файл на рабочем столе именем **Users.csv**.<br/>

5. Откройте новый экземпляр Блокнота и вставьте в него следующий блок текста:<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>Где MyAlias — имя пользователя, вошедшего в систему.<br/>

6. Сохраните файл на рабочем столе как **UsersAndGroups.ps1**. Это простое сценария Windows PowerShell.

Теперь вы можете выполнить скрипт UsersAndGroup.ps1, чтобы добавить пользователей и группы в несколько семейств сайтов.

### <a name="run-usersandgroupsps1-script"></a>Выполнение скрипта UsersAndGroups.ps1

1. Вернитесь в командную консоль SharePoint Online.<br/>
2. В командной строке Windows PowerShell введите или скопируйте и вставьте следующую строку, а затем нажмите клавишу ВВОД:<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. В окне подтверждения нажмите клавишу **Y**.<br/>

4. В командной строке Windows PowerShell введите и или скопируйте и вставьте следующую строку, а затем нажмите клавишу ВВОД:<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>Где *MyAlias* — это имя пользователя.<br/>

5. Дождитесь появления окна командной строки. Сначала вы увидите группы по мере их создания. Затем вы увидите список групп, который повторяется при добавлении пользователей.

## <a name="see-also"></a>См. также

[Подключение к PowerShell в SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Управление группами SharePoint Online сайт Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

