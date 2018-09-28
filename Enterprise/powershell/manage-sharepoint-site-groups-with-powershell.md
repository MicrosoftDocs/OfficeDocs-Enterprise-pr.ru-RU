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
ms.openlocfilehash: c68e0905c0abcbea279829be7c841c31409db6cf
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975147"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="ec75c-103">Управление группами сайтов SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec75c-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="ec75c-104">**Сводка:** Использование Office 365 PowerShell для управления SharePoint Online группы сайтов.</span><span class="sxs-lookup"><span data-stu-id="ec75c-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="ec75c-105">Несмотря на то, что можно использовать Центр администрирования Office 365, можно также использовать Office 365 PowerShell для управления SharePoint Online групп сайта.</span><span class="sxs-lookup"><span data-stu-id="ec75c-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ec75c-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="ec75c-106">Before you begin</span></span>

<span data-ttu-id="ec75c-p101">Процедуры, описанные в этой статье требуется подключение к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="ec75c-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="ec75c-109">Просмотр SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec75c-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="ec75c-p102">Центр администрирования SharePoint Online имеет некоторые простые в использовании методы для управления группами сайтов. Предположим, например, чтобы посмотреть на группы и участники групп, `https://litwareinc.sharepoint.com/sites/finance` сайта. Вот что необходимо сделать, чтобы:</span><span class="sxs-lookup"><span data-stu-id="ec75c-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="ec75c-113">В центре администрирования Office 365 щелкните **ресурсы** > **сайтов**и затем щелкните URL-адрес сайта.</span><span class="sxs-lookup"><span data-stu-id="ec75c-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="ec75c-114">В диалоговом окне Семейство веб-сайтов выберите **Перейти на сайт**.</span><span class="sxs-lookup"><span data-stu-id="ec75c-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="ec75c-115">На странице сайта щелкните значок **Параметры** (в верхнем правом углу страницы) и нажмите кнопку **Параметры сайта**.</span><span class="sxs-lookup"><span data-stu-id="ec75c-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span><br/>
<span data-ttu-id="ec75c-116">![SharePoint Online параметры сайта](media/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="ec75c-116">![SharePoint Online site settings](media/spo-site-settings.png)</span></span><br/>
4. <span data-ttu-id="ec75c-117">На странице "Параметры узла" щелкните **разрешения сайтов** в разделе **пользователи и разрешения**.</span><span class="sxs-lookup"><span data-stu-id="ec75c-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="ec75c-118">И затем повторить процесс для следующего сайта, который необходимо просмотреть.</span><span class="sxs-lookup"><span data-stu-id="ec75c-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="ec75c-119">Чтобы получить список групп с помощью Office 365 PowerShell, используйте следующий набор команд:</span><span class="sxs-lookup"><span data-stu-id="ec75c-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="ec75c-120">Для выполнения этой команды в командной консоли SharePoint Online двумя способами:</span><span class="sxs-lookup"><span data-stu-id="ec75c-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="ec75c-p103">Скопируйте команд в "Блокнот" (или другом текстовом редакторе), измените значение переменной **$siteURL** , выберите команды и вставьте их в командной консоли SharePoint Online. В этом случае PowerShell будет останавливаться на **>>** строки. Нажмите клавишу ВВОД, чтобы выполнить команду **foreach** .</span><span class="sxs-lookup"><span data-stu-id="ec75c-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a **>>** prompt. Press Enter to execute the **foreach** command.</span></span><br/>
- <span data-ttu-id="ec75c-p104">Скопируйте команд в "Блокнот" (или другом текстовом редакторе), измените значение переменной **$siteURL** и затем сохраните этот текстовый файл с именем и расширение ".ps1" в соответствующие папки. Затем выполните скрипт в командной консоли SharePoint Online, указав его путь и имя файла. Ниже приведен пример команды.</span><span class="sxs-lookup"><span data-stu-id="ec75c-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="ec75c-127">В обоих случаях должно отобразиться что-то вроде этого:</span><span class="sxs-lookup"><span data-stu-id="ec75c-127">In both cases, you should see something similar to this:</span></span>

![SharePoint Online группы сайтов](media/SPO-site-groups.png)

<span data-ttu-id="ec75c-p105">Далее представлены все группы, которые были созданы для сайта `https://litwareinc.sharepoint.com/sites/finance`, также все пользователи, которым назначены этим группам. Имена групп — желтого цвета, которые помогут вам имена другая группа от их участников.</span><span class="sxs-lookup"><span data-stu-id="ec75c-p105">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="ec75c-131">Другой пример: Вот набор команд, содержит список групп и всех членство в группах, для всех сайтов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ec75c-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a><span data-ttu-id="ec75c-132">См. также</span><span class="sxs-lookup"><span data-stu-id="ec75c-132">See also</span></span>

[<span data-ttu-id="ec75c-133">Подключение к PowerShell в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec75c-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="ec75c-134">Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec75c-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

<span data-ttu-id="ec75c-135">[Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="ec75c-135">[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)</span></span>

[<span data-ttu-id="ec75c-136">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="ec75c-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ec75c-137">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec75c-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

