---
title: Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Сводка: Использование Office 365 PowerShell для управления SharePoint Online пользователями, группами и сайтами.'
ms.openlocfilehash: a04bf1538d6f56b760932b5be89b1953fcaa33d5
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell

 **Сводка:** Использование Office 365 PowerShell для управления SharePoint Online пользователей, групп и сайтов.

Если вы являетесь администратором SharePoint Online, для работы с большими списками учетных записей пользователей или групп, а также выполнить более простой способ управления ими, можно использовать Office 365 PowerShell. 

## <a name="before-you-begin"></a>Перед началом работы

Процедуры, описанные в этом разделе требуется подключение к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>Получение списков сайтов, групп и пользователей

Прежде чем мы начнем управлять пользователями и группами, вам необходимо получить список сайтов, групп и пользователей. Эту информацию можно использовать для работы с примером в данной статье.

### <a name="get-a-list-of-sites"></a>Получение списка сайтов

Чтобы получить список сайтов в своем клиенте, выполните следующую команду:

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>Получение списка групп

Чтобы получить список групп в своем клиенте, выполните следующую команду:

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a>Получение списка пользователей

Чтобы получить список пользователей в своем клиенте, выполните следующую команду:

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Добавление пользователя в группу администраторов семейства веб-сайтов

Команда **Set-SPOUser** для добавления пользователя в список администраторов семейства сайтов в семействе сайтов. Это, как будет выглядеть следующий синтаксис:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

Чтобы использовать эти команды, заменить замените все содержимое в кавычки, включая < и > символы с правильные имена.

К примеру этот набор команд добавляет Opal Castillo (opalc имени пользователя) список Администраторы семейства сайтов в семействе сайтов ContosoTest в клиенте contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

Можно скопировать и вставить эти команды в блокноте, измените значения переменных для $tenant, $site и $user фактических значений из среды и вставить скрипт в вашем окне Командная консоль SharePoint Online для их запуска.

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>Добавление пользователя в другие группы администраторов семейства веб-сайтов

В этой задаче будет использовать команду **Add-SPOUser** для добавления пользователя в группу SharePoint в семействе сайтов.

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

Например добавим Rife Glen (glenr имени пользователя) группе аудиторов на семейства сайтов ContosoTest в клиенте contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Создание группы семейства веб-сайтов

Команда **Set-SPOSiteGroup** используется для создания новой группы SharePoint и добавить его в семейство сайтов ContosoTest.

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
Группируйте свойства, такие как уровни разрешений можно было обновить с помощью командлета **Set-SPOSiteGroup** .

Например добавим аудиторы группы с разрешениями только просмотр Contoso тестовых семейства веб-сайтов в клиенте contoso1:

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Удаление пользователей из группы

Иногда необходимо удалить пользователя с сайта или даже со всех сайтов. Возможно, сотрудник переводится из одного подразделения в другое или увольняется из компании. Одного сотрудника можно легко удалить в пользовательском интерфейсе, однако не так-то просто перенести целое подразделение с одного сайта на другой.

Однако с помощью файлов Командная консоль SharePoint Online и CSV, это легко и быстро. В этой задаче будет использовать Windows PowerShell для удаления пользователя из группы безопасности семейства сайтов. Затем можно использовать в CSV-файл и удаление большое количество пользователей на различных сайтах. 

Мы будем использование команды **Remove-SPOUser** для удаления отдельному пользователю Office 365 из группы семейства сайтов только в том случае, поэтому можно увидеть синтаксис команды. В этом разделе представлен следующий синтаксис:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
Например давайте удалить Bobby Overby из группы аудиторов семейства сайтов в семействе сайтов тестирования Contoso в клиенте contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Предположим, что мы хотим удалить Bobby из всех групп, в которых он состоит. Вот как это сделать:

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> Это лишь пример. Не следует запускать эту команду, если не нужно удалить пользователя из каждой группы, например, если пользователь покидает компанию.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Автоматизация управления большими списками пользователей и групп

Чтобы добавить большое число учетных записей для сайтов SharePoint и предоставьте им разрешения, можно использовать Центр администрирования Office 365, отдельные команды PowerShell или PowerShell в CSV-файл. Эти варианты выбора CSV-файл является быстрым способом для автоматизации этой задачи.

Базовый процесс заключается в создании CSV-файл, который есть заголовки (столбцы), которые соответствуют параметрам, которые должен сценарий Windows PowerShell. Можно легко создавать такой список в Excel и его экспорта в CSV-файл. Затем используйте сценарий Windows PowerShell для итерации записей (строк) в CSV-файл, добавление пользователей в группы и группы к сайтам. 

Для примера создадим CSV-файл, чтобы определить группу семейств сайтов, групп и разрешений. Затем мы создадим CSV-файл, чтобы заполнить группы пользователями. Наконец, мы создадим и выполним простой скрипт Windows PowerShell, который создает и заполняет группы.

Первый CSV-файл добавляет одну или несколько групп в одно или несколько семейств сайтов. Он использует следующую структуру:

### <a name="header"></a>Заголовок:

```
Site,Group,PermissionLevels
```

### <a name="item"></a>Элемент:

```
https://tenant.sharepoint.com/sites/site,group,level
```

Ниже приведен пример файла:

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

Второй CSV-файл добавляет одного или нескольких пользователей в одну или несколько групп. Он использует следующую структуру:

### <a name="header"></a>Заголовок:

```
Group,LoginName,Site
```

### <a name="item"></a>Элемент:

```
group,login,https://tenant.sharepoint.com/sites/site
```

Ниже приведен пример файла:

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

Для следующего шага необходимо иметь два CSV-файлы на диске. Ниже приведены примеры команд, использующих оба файла CSV и для добавления разрешений и членства:

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Сценарий импортирует содержимое файла CSV и использует значения в столбцах для заполнения параметров команды **New-SPOSiteGroup** и **Add-SPOUser** . В нашем примере мы сохраняете это theO365Admin папку на диске C, но его можно сохранить там, где хотите.

Теперь давайте удалить группу людей для нескольких групп в различных сайтов с помощью же CSV-файл. Ниже приведен пример команды.

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Создание отчетов о пользователях

Возможно, вам потребуется простой отчет о пользователях нескольких сайтов, их уровне разрешений и других свойствах. Вот как выглядит синтаксис команды:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Это взять данные для этих трех сайтов и записать их в текстовый файл на локальном диске. Обратите внимание, что параметр – Append будет добавления нового контента в существующий файл.

Например, запустим отчет на сайтах ContosoTest, TeamSite01 и Project01 клиентской организации Contoso1.

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Обратите внимание, что у нас изменение только переменной **$site** . Переменная **$tenant** сохраняет свое значение через все три выполнения команды.

Но что делать, если вы хотите сделать это для каждого сайта? Используйте эту команду, чтобы не вводить все нужные веб-сайты:

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

В этом отчете довольно прост, и можно добавить дополнительный код для создания более подробные отчеты или отчеты, содержащие более подробные сведения. Однако это должно дать о том, как использовать командную консоль SharePoint Online для управления пользователями в среде SharePoint Online.
   
## <a name="see-also"></a>См. также

[Подключение к SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Управление SharePoint Online с помощью Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

