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
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="d93a4-103">Управление группами сайтов SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d93a4-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="d93a4-104">**Сводка:** Использование Office 365 PowerShell для управления SharePoint Online группы сайтов.</span><span class="sxs-lookup"><span data-stu-id="d93a4-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="d93a4-105">Несмотря на то, что можно использовать Центр администрирования Office 365, можно также использовать Office 365 PowerShell для управления SharePoint Online групп сайта.</span><span class="sxs-lookup"><span data-stu-id="d93a4-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d93a4-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="d93a4-106">Before you begin</span></span>

<span data-ttu-id="d93a4-p101">Процедуры, описанные в этой статье требуется подключение к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="d93a4-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="d93a4-109">Просмотр SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d93a4-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="d93a4-p102">Центр администрирования SharePoint Online имеет некоторые простые в использовании методы для управления группами сайтов. Предположим, например, чтобы посмотреть на группы и участники групп, https://litwareinc.sharepoint.com/sites/finance сайта. Вот что необходимо сделать, чтобы:</span><span class="sxs-lookup"><span data-stu-id="d93a4-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="d93a4-113">В центре администрирования Office 365 щелкните **ресурсы** > **сайтов**и затем щелкните URL-адрес сайта.</span><span class="sxs-lookup"><span data-stu-id="d93a4-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="d93a4-114">В диалоговом окне семейства сайтов нажмите кнопку **Перейти на этом сайте**.</span><span class="sxs-lookup"><span data-stu-id="d93a4-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="d93a4-115">На странице "сайт" щелкните значок **Параметры** (находится в правом верхнем углу страницы) и выберите пункт **Параметры сайта**:</span><span class="sxs-lookup"><span data-stu-id="d93a4-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="d93a4-116">![SharePoint Online параметры сайта](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="d93a4-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="d93a4-117">На странице "Параметры узла" щелкните **разрешения сайтов** в разделе **пользователи и разрешения**.</span><span class="sxs-lookup"><span data-stu-id="d93a4-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="d93a4-118">И затем повторить процесс для следующего сайта, который необходимо просмотреть.</span><span class="sxs-lookup"><span data-stu-id="d93a4-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="d93a4-119">Чтобы получить список групп с помощью Office 365 PowerShell, используйте следующий набор команд:</span><span class="sxs-lookup"><span data-stu-id="d93a4-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="d93a4-120">Для выполнения этой команды в командной консоли SharePoint Online двумя способами:</span><span class="sxs-lookup"><span data-stu-id="d93a4-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>
- <span data-ttu-id="d93a4-p103">Скопируйте команд в "Блокнот" (или другом текстовом редакторе), измените значение переменной **$siteURL** , выберите команды и вставьте их в командной консоли SharePoint Online. В этом случае PowerShell будет останавливаться на >> строки. Нажмите клавишу ВВОД, чтобы выполнить для каждой команды.</span><span class="sxs-lookup"><span data-stu-id="d93a4-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a >> prompt. Press Enter to execute the for each command.</span></span></br>
- <span data-ttu-id="d93a4-p104">Скопируйте команд в "Блокнот" (или другом текстовом редакторе), измените значение переменной **$siteURL** и затем сохраните этот текстовый файл с именем и расширение ".ps1" в соответствующие папки. Затем выполните скрипт в командной консоли SharePoint Online, указав его путь и имя файла. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="d93a4-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example:</span></span></br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
<span data-ttu-id="d93a4-127">$x = get-SPOSite foreach ($y в $x) {$y.Url Write-Host - ForegroundColor «желтый» $z = Get-SPOSiteGroup-foreach $y.Url сайта ($ в $z) {$b = Get-SPOSiteGroup-веб-$y.Url-$b.Title $a.Title записи узла группы - ForegroundColor «Голубой» $b | SELECT-Object - ExpandProperty пользователей Write-Host}}</span><span class="sxs-lookup"><span data-stu-id="d93a4-127">$x = Get-SPOSite foreach ($y in $x) { Write-Host $y.Url -ForegroundColor "Yellow" $z = Get-SPOSiteGroup -Site $y.Url foreach ($a in $z) { $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title Write-Host $b.Title -ForegroundColor "Cyan" $b | Select-Object -ExpandProperty Users Write-Host } }</span></span>
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

