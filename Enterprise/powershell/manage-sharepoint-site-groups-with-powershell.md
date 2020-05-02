---
title: Управление группами сайтов SharePoint Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
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
description: 'Сводка: использование PowerShell в Office 365 для управления группами сайтов SharePoint Online.'
ms.openlocfilehash: 3a1b999470746cbe02ec52fe888ea26b59cd423b
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004202"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="48e9b-103">Управление группами сайтов SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="48e9b-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="48e9b-104">Несмотря на то что вы можете использовать центр администрирования Microsoft 365, вы также можете использовать Office 365 PowerShell для управления группами сайтов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="48e9b-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="48e9b-105">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="48e9b-105">Before you begin</span></span>

<span data-ttu-id="48e9b-106">Процедуры, описанные в этой статье, требуют подключения к SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="48e9b-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="48e9b-107">Инструкции см. в статье [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="48e9b-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="48e9b-108">Просмотр SharePoint Online с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="48e9b-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="48e9b-109">В центре администрирования SharePoint Online есть несколько простых в использовании способов управления группами сайтов.</span><span class="sxs-lookup"><span data-stu-id="48e9b-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="48e9b-110">Например, предположим, что вы хотите просмотреть группы и членов группы для `https://litwareinc.sharepoint.com/sites/finance` сайта.</span><span class="sxs-lookup"><span data-stu-id="48e9b-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="48e9b-111">Вот как это сделать.</span><span class="sxs-lookup"><span data-stu-id="48e9b-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="48e9b-112">В центре администрирования SharePoint щелкните **активные сайты**, а затем щелкните URL-адрес сайта.</span><span class="sxs-lookup"><span data-stu-id="48e9b-112">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="48e9b-113">На странице сайт щелкните значок **Параметры** (в верхнем правом углу страницы), а затем выберите **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="48e9b-113">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="48e9b-114">И затем повторить процесс для следующего сайта, который необходимо просмотреть.</span><span class="sxs-lookup"><span data-stu-id="48e9b-114">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="48e9b-115">Чтобы получить список групп с помощью Office 365 PowerShell, можно использовать следующие команды:</span><span class="sxs-lookup"><span data-stu-id="48e9b-115">To get a list of the groups with Office 365 PowerShell, you can use the following commands:</span></span>

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="48e9b-116">Существует два способа выполнения этого набора команд в командной строке командной консоли SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="48e9b-116">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="48e9b-117">Скопируйте команды в Блокнот (или другой текстовый редактор), измените значение переменной **$siteURL** , выберите команды, а затем вставьте их в командную строку консоли управления SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="48e9b-117">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="48e9b-118">После этого PowerShell остановится в **>>** командной консоли.</span><span class="sxs-lookup"><span data-stu-id="48e9b-118">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="48e9b-119">Нажмите клавишу ВВОД, `foreach` чтобы выполнить команду.</span><span class="sxs-lookup"><span data-stu-id="48e9b-119">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="48e9b-120">Скопируйте команды в блокнот (или другой текстовый редактор), измените значение переменной **$siteURL**, а затем сохраните этот текстовый файл с именем и расширением .ps1 в подходящей папке.</span><span class="sxs-lookup"><span data-stu-id="48e9b-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="48e9b-121">После этого запустите сценарий из командной строки командной консоли SharePoint Online, указав путь и имя файла.</span><span class="sxs-lookup"><span data-stu-id="48e9b-121">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="48e9b-122">Вот пример необходимой команды:</span><span class="sxs-lookup"><span data-stu-id="48e9b-122">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="48e9b-123">В обоих случаях должно отобразиться что-то вроде этого:</span><span class="sxs-lookup"><span data-stu-id="48e9b-123">In both cases, you should see something similar to this:</span></span>

![Группы сайтов SharePoint Online](media/SPO-site-groups.png)

<span data-ttu-id="48e9b-125">Это все группы, созданные для сайта `https://litwareinc.sharepoint.com/sites/finance`, и все пользователи, назначенные этим группам.</span><span class="sxs-lookup"><span data-stu-id="48e9b-125">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="48e9b-126">Имена групп обозначены желтым цветом, чтобы вы могли отличить имена групп от их участников.</span><span class="sxs-lookup"><span data-stu-id="48e9b-126">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="48e9b-127">Другой пример: набор команд, в котором перечислены группы и все сведения о членстве в группах для всех сайтов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="48e9b-127">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```powershell
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
    
## <a name="see-also"></a><span data-ttu-id="48e9b-128">См. также</span><span class="sxs-lookup"><span data-stu-id="48e9b-128">See also</span></span>

[<span data-ttu-id="48e9b-129">Подключение к PowerShell в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="48e9b-129">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="48e9b-130">Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="48e9b-130">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

<span data-ttu-id="48e9b-131">[Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="48e9b-131">[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)</span></span>

[<span data-ttu-id="48e9b-132">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="48e9b-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="48e9b-133">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="48e9b-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

