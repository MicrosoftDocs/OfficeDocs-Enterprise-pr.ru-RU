---
title: Управление группами сайтов SharePoint Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Сводка: Использование Office 365 PowerShell для управления SharePoint Online группы сайтов.'
ms.openlocfilehash: 68be9ce3ef26cb46df6d43716c6719ffd9c172e2
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Управление группами сайтов SharePoint Online с помощью Office 365 PowerShell

 **Сводка:** Использование Office 365 PowerShell для управления SharePoint Online группы сайтов.
  
Несмотря на то, что можно использовать Центр администрирования Office 365, можно также использовать Office 365 PowerShell для управления SharePoint Online групп сайта.

## <a name="before-you-begin"></a>Перед началом работы

Процедуры, описанные в этой статье требуется подключение к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Просмотр SharePoint Online с помощью Office 365 PowerShell

Центр администрирования SharePoint Online имеет некоторые простые в использовании методы для управления группами сайтов. Предположим, например, чтобы посмотреть на группы и участники групп, https://litwareinc.sharepoint.com/sites/finance сайта. Вот что необходимо сделать, чтобы:

1. В центре администрирования Office 365 щелкните **ресурсы** > **сайтов**и затем щелкните URL-адрес сайта.
2. В диалоговом окне семейства сайтов нажмите кнопку **Перейти на этом сайте**.
3. На странице "сайт" щелкните значок **Параметры** (находится в правом верхнем углу страницы) и выберите пункт **Параметры сайта**:</br>
![SharePoint Online параметры сайта](images/spo-site-settings.png)</br>
4. На странице "Параметры узла" щелкните **разрешения сайтов** в разделе **пользователи и разрешения**.

И затем повторить процесс для следующего сайта, который необходимо просмотреть.

Чтобы получить список групп с помощью Office 365 PowerShell, используйте следующий набор команд:

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Для выполнения этой команды в командной консоли SharePoint Online двумя способами:
- Скопируйте команд в "Блокнот" (или другом текстовом редакторе), измените значение переменной **$siteURL** , выберите команды и вставьте их в командной консоли SharePoint Online. В этом случае PowerShell будет останавливаться на >> строки. Нажмите клавишу ВВОД, чтобы выполнить для каждой команды.</br>
- Скопируйте команд в "Блокнот" (или другом текстовом редакторе), измените значение переменной **$siteURL** и затем сохраните этот текстовый файл с именем и расширение ".ps1" в соответствующие папки. Затем выполните скрипт в командной консоли SharePoint Online, указав его путь и имя файла. Ниже приведен пример:</br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
$x = get-SPOSite foreach ($y в $x) {$y.Url Write-Host - ForegroundColor «желтый» $z = Get-SPOSiteGroup-foreach $y.Url сайта ($ в $z) {$b = Get-SPOSiteGroup-веб-$y.Url-$b.Title $a.Title записи узла группы - ForegroundColor «Голубой» $b | SELECT-Object - ExpandProperty пользователей Write-Host}}
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

