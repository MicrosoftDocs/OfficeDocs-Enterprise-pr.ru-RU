---
title: Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Сводка: использование PowerShell в Office 365 для создания новых сайтов SharePoint Online и добавления пользователей и групп на эти сайты.'
ms.openlocfilehash: 8011a7e3f61e6b26d4606bfdae67152a1d894840
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735707"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell

Когда вы используете Office 365 PowerShell для создания сайтов SharePoint Online и добавления пользователей, вы можете быстро и многократно выполнять задачи гораздо быстрее, чем в центре администрирования Майкрософт 365. Вы также можете выполнять задачи, которые невозможно выполнить в центре администрирования Office 365. 

## <a name="before-you-begin"></a>Перед началом работы

Процедуры, описанные в этом разделе, требуют подключения к SharePoint Online. Инструкции см в разделе [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Шаг 1. Создание семейств веб-сайтов с помощью Office 365 PowerShell

Создайте несколько сайтов с помощью PowerShell для Office 365 и CSV-файла, созданного с помощью примера кода и блокнота. В этой процедуре заменяются сведения о заполнителе, показанные в квадратных скобках, с собственными сведениями о сайтах и клиентах. Этот процесс позволяет создать один файл и запустить одну команду PowerShell Office 365, использующую этот файл. Это делает действия, которые были как повторяющимися, так и переносимыми, и исключает многие, если не все, ошибки, которые могут возникнуть при вводе длинных команд в командную консоль SharePoint Online. Эта процедура состоит из двух частей. Сначала вы создадите CSV-файл, а затем сослаться на этот CSV-файл с помощью Office 365 PowerShell, который будет использовать его содержимое для создания сайтов.

The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.

### <a name="create-a-csv-file"></a>Создание CSV-файла

1. Откройте Блокнот и вставьте в него следующий блок текста:<br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>Где *клиент* — это имя вашего клиента, а *owner* — это имя пользователя в клиенте, которому требуется предоставить роль главного администратора семейства веб-сайтов.<br/>(Можно нажать клавиши CTRL + H при использовании блокнота для ускорения массового замещения.)<br/>

2. Сохраните файл на рабочем столе как **SiteCollections.csv**.<br/>

> [!TIP]
> Перед использованием этого или другого файла сценария. CSV или Windows PowerShell рекомендуется убедиться в отсутствии лишних или непечатаемых символов. Откройте файл в Word и щелкните значок абзаца на ленте, чтобы показать непечатаемые символы. Файлы не должны содержать лишние непечатаемые символы. Например, в конце файла не должно быть знаков абзаца.

### <a name="run-the-windows-powershell-command"></a>Выполнение команды Windows PowerShell

1. В командной консоли Windows PowerShell введите (или скопируйте и вставьте) следующую команду и нажмите клавишу ВВОД:<br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>Где *мялиас* соответствует псевдониму пользователя.<br/>

2. Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.<br/>

3. В командной строке Windows PowerShell введите или скопируйте и вставьте следующий командлет, а затем нажмите клавишу ВВОД:<br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. Обратите внимание на новые семейства веб-сайтов в списке. Используя наш пример CSV-файла, вы увидите следующие семейства веб-сайтов: **TeamSite01**, **Blog01**, **Project01**и **Community01**

Вот и все. Вы создали несколько семейств веб-сайтов с помощью созданного CSV-файла и одной команды Windows PowerShell. Теперь вы можете создать пользователей и назначить их сайтам.

## <a name="step-2-add-users-and-groups"></a>Действие 2. Добавление пользователей или групп

Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.

Следующие процедуры продолжают использовать примеры сайтов TeamSite01, Blog01, Project01 и Community01.

### <a name="create-csv-and-ps1-files"></a>Создание CSV- и PS1-файлов

1. Откройте Блокнот и вставьте в него следующий блок текста:<br/>

```powershell
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>Где *клиент* равняется имени клиента.<br/>

2. Сохраните файл на рабочем столе как **GroupsAndPermissions.csv**.<br/>

3. Откройте новый экземпляр Блокнота и вставьте в него следующий блок текста:<br/>

```powershell
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>Где *клиент* равняется имени клиента, а *username* — имя пользователя существующего пользователя.<br/>

4. Сохраните файл на рабочем столе как **Users.csv**.<br/>

5. Откройте новый экземпляр Блокнота и вставьте в него следующий блок текста:<br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>Где Мялиас = имя пользователя, выполнившего вход в систему.<br/>

6. Сохраните файл на рабочем столе как **UsersAndGroups.ps1**. Это простой сценарий Windows PowerShell.

Теперь вы можете выполнить скрипт UsersAndGroup.ps1, чтобы добавить пользователей и группы в несколько семейств сайтов.

### <a name="run-usersandgroupsps1-script"></a>Выполнение скрипта UsersAndGroups.ps1

1. Вернитесь в командную консоль SharePoint Online.<br/>
2. В командной строке Windows PowerShell введите или скопируйте и вставьте следующую строку, а затем нажмите клавишу ВВОД:<br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. В запросе подтверждения нажмите **Y**.<br/>

4. В командной строке Windows PowerShell введите и или скопируйте и вставьте следующую строку, а затем нажмите клавишу ВВОД:<br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>Где *мялиас* = ваше имя пользователя.<br/>

5. Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.

## <a name="see-also"></a>См. также

[Подключение к PowerShell в SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Управление группами сайтов SharePoint Online в Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Управление Office 365 с помощью Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

