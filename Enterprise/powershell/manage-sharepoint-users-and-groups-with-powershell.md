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
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="7ef11-103">Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ef11-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="7ef11-104">**Сводка:** Использование Office 365 PowerShell для управления SharePoint Online пользователей, групп и сайтов.</span><span class="sxs-lookup"><span data-stu-id="7ef11-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="7ef11-105">Если вы являетесь администратором SharePoint Online, для работы с большими списками учетных записей пользователей или групп, а также выполнить более простой способ управления ими, можно использовать Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ef11-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="7ef11-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="7ef11-106">Before you begin</span></span>

<span data-ttu-id="7ef11-p101">Процедуры, описанные в этом разделе требуется подключение к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="7ef11-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="7ef11-109">Получение списков сайтов, групп и пользователей</span><span class="sxs-lookup"><span data-stu-id="7ef11-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="7ef11-p102">Прежде чем мы начнем управлять пользователями и группами, вам необходимо получить список сайтов, групп и пользователей. Эту информацию можно использовать для работы с примером в данной статье.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="7ef11-112">Получение списка сайтов</span><span class="sxs-lookup"><span data-stu-id="7ef11-112">Get a list of sites</span></span>

<span data-ttu-id="7ef11-113">Чтобы получить список сайтов в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="7ef11-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="7ef11-114">Получение списка групп</span><span class="sxs-lookup"><span data-stu-id="7ef11-114">Get a list of groups</span></span>

<span data-ttu-id="7ef11-115">Чтобы получить список групп в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="7ef11-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="7ef11-116">Получение списка пользователей</span><span class="sxs-lookup"><span data-stu-id="7ef11-116">Get a list of users</span></span>

<span data-ttu-id="7ef11-117">Чтобы получить список пользователей в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="7ef11-117">Get a list of the users in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="7ef11-118">Добавление пользователя в группу администраторов семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="7ef11-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="7ef11-p103">Команда **Set-SPOUser** для добавления пользователя в список администраторов семейства сайтов в семействе сайтов. Это, как будет выглядеть следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="7ef11-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="7ef11-121">Чтобы использовать эти команды, заменить замените все содержимое в кавычки, включая < и > символы с правильные имена.</span><span class="sxs-lookup"><span data-stu-id="7ef11-121">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="7ef11-122">К примеру этот набор команд добавляет Opal Castillo (opalc имени пользователя) список Администраторы семейства сайтов в семействе сайтов ContosoTest в клиенте contoso1:</span><span class="sxs-lookup"><span data-stu-id="7ef11-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="7ef11-123">Можно скопировать и вставить эти команды в блокноте, измените значения переменных для $tenant, $site и $user фактических значений из среды и вставить скрипт в вашем окне Командная консоль SharePoint Online для их запуска.</span><span class="sxs-lookup"><span data-stu-id="7ef11-123">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="7ef11-124">Добавление пользователя в другие группы администраторов семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="7ef11-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="7ef11-125">В этой задаче будет использовать команду **Add-SPOUser** для добавления пользователя в группу SharePoint в семействе сайтов.</span><span class="sxs-lookup"><span data-stu-id="7ef11-125">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="7ef11-126">Например добавим Rife Glen (glenr имени пользователя) группе аудиторов на семейства сайтов ContosoTest в клиенте contoso1:</span><span class="sxs-lookup"><span data-stu-id="7ef11-126">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="7ef11-127">Создание группы семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="7ef11-127">Create a site collection group</span></span>

<span data-ttu-id="7ef11-128">Команда **Set-SPOSiteGroup** используется для создания новой группы SharePoint и добавить его в семейство сайтов ContosoTest.</span><span class="sxs-lookup"><span data-stu-id="7ef11-128">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="7ef11-129">Группируйте свойства, такие как уровни разрешений можно было обновить с помощью командлета **Set-SPOSiteGroup** .</span><span class="sxs-lookup"><span data-stu-id="7ef11-129">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="7ef11-130">Например добавим аудиторы группы с разрешениями только просмотр Contoso тестовых семейства веб-сайтов в клиенте contoso1:</span><span class="sxs-lookup"><span data-stu-id="7ef11-130">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="7ef11-131">Удаление пользователей из группы</span><span class="sxs-lookup"><span data-stu-id="7ef11-131">Remove users from a group</span></span>

<span data-ttu-id="7ef11-p104">Иногда необходимо удалить пользователя с сайта или даже со всех сайтов. Возможно, сотрудник переводится из одного подразделения в другое или увольняется из компании. Одного сотрудника можно легко удалить в пользовательском интерфейсе, однако не так-то просто перенести целое подразделение с одного сайта на другой.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p104">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="7ef11-p105">Однако с помощью файлов Командная консоль SharePoint Online и CSV, это легко и быстро. В этой задаче будет использовать Windows PowerShell для удаления пользователя из группы безопасности семейства сайтов. Затем можно использовать в CSV-файл и удаление большое количество пользователей на различных сайтах.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p105">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="7ef11-p106">Мы будем использование команды **Remove-SPOUser** для удаления отдельному пользователю Office 365 из группы семейства сайтов только в том случае, поэтому можно увидеть синтаксис команды. В этом разделе представлен следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="7ef11-p106">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="7ef11-140">Например давайте удалить Bobby Overby из группы аудиторов семейства сайтов в семействе сайтов тестирования Contoso в клиенте contoso1:</span><span class="sxs-lookup"><span data-stu-id="7ef11-140">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="7ef11-p107">Предположим, что мы хотим удалить Bobby из всех групп, в которых он состоит. Вот как это сделать:</span><span class="sxs-lookup"><span data-stu-id="7ef11-p107">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="7ef11-p108">Это лишь пример. Не следует запускать эту команду, если не нужно удалить пользователя из каждой группы, например, если пользователь покидает компанию.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p108">This is just an example. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="7ef11-145">Автоматизация управления большими списками пользователей и групп</span><span class="sxs-lookup"><span data-stu-id="7ef11-145">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="7ef11-p109">Чтобы добавить большое число учетных записей для сайтов SharePoint и предоставьте им разрешения, можно использовать Центр администрирования Office 365, отдельные команды PowerShell или PowerShell в CSV-файл. Эти варианты выбора CSV-файл является быстрым способом для автоматизации этой задачи.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p109">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="7ef11-p110">Базовый процесс заключается в создании CSV-файл, который есть заголовки (столбцы), которые соответствуют параметрам, которые должен сценарий Windows PowerShell. Можно легко создавать такой список в Excel и его экспорта в CSV-файл. Затем используйте сценарий Windows PowerShell для итерации записей (строк) в CSV-файл, добавление пользователей в группы и группы к сайтам.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p110">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="7ef11-p111">Для примера создадим CSV-файл, чтобы определить группу семейств сайтов, групп и разрешений. Затем мы создадим CSV-файл, чтобы заполнить группы пользователями. Наконец, мы создадим и выполним простой скрипт Windows PowerShell, который создает и заполняет группы.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p111">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="7ef11-154">Первый CSV-файл добавляет одну или несколько групп в одно или несколько семейств сайтов. Он использует следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="7ef11-154">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="7ef11-155">Заголовок:</span><span class="sxs-lookup"><span data-stu-id="7ef11-155">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="7ef11-156">Элемент:</span><span class="sxs-lookup"><span data-stu-id="7ef11-156">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="7ef11-157">Ниже приведен пример файла:</span><span class="sxs-lookup"><span data-stu-id="7ef11-157">Here is an example file:</span></span>

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

<span data-ttu-id="7ef11-158">Второй CSV-файл добавляет одного или нескольких пользователей в одну или несколько групп. Он использует следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="7ef11-158">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="7ef11-159">Заголовок:</span><span class="sxs-lookup"><span data-stu-id="7ef11-159">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="7ef11-160">Элемент:</span><span class="sxs-lookup"><span data-stu-id="7ef11-160">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="7ef11-161">Ниже приведен пример файла:</span><span class="sxs-lookup"><span data-stu-id="7ef11-161">Here is an example file:</span></span>

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

<span data-ttu-id="7ef11-p112">Для следующего шага необходимо иметь два CSV-файлы на диске. Ниже приведены примеры команд, использующих оба файла CSV и для добавления разрешений и членства:</span><span class="sxs-lookup"><span data-stu-id="7ef11-p112">For the next step, you must have the two CSV files saved to your drive. Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="7ef11-p113">Сценарий импортирует содержимое файла CSV и использует значения в столбцах для заполнения параметров команды **New-SPOSiteGroup** и **Add-SPOUser** . В нашем примере мы сохраняете это theO365Admin папку на диске C, но его можно сохранить там, где хотите.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p113">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="7ef11-p114">Теперь давайте удалить группу людей для нескольких групп в различных сайтов с помощью же CSV-файл. Ниже приведен пример команды.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p114">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is an example command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="7ef11-168">Создание отчетов о пользователях</span><span class="sxs-lookup"><span data-stu-id="7ef11-168">Generate user reports</span></span>

<span data-ttu-id="7ef11-p115">Возможно, вам потребуется простой отчет о пользователях нескольких сайтов, их уровне разрешений и других свойствах. Вот как выглядит синтаксис команды:</span><span class="sxs-lookup"><span data-stu-id="7ef11-p115">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="7ef11-p116">Это взять данные для этих трех сайтов и записать их в текстовый файл на локальном диске. Обратите внимание, что параметр – Append будет добавления нового контента в существующий файл.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p116">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="7ef11-173">Например, запустим отчет на сайтах ContosoTest, TeamSite01 и Project01 клиентской организации Contoso1.</span><span class="sxs-lookup"><span data-stu-id="7ef11-173">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="7ef11-p117">Обратите внимание, что у нас изменение только переменной **$site** . Переменная **$tenant** сохраняет свое значение через все три выполнения команды.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p117">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="7ef11-p118">Но что делать, если вы хотите сделать это для каждого сайта? Используйте эту команду, чтобы не вводить все нужные веб-сайты:</span><span class="sxs-lookup"><span data-stu-id="7ef11-p118">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="7ef11-p119">В этом отчете довольно прост, и можно добавить дополнительный код для создания более подробные отчеты или отчеты, содержащие более подробные сведения. Однако это должно дать о том, как использовать командную консоль SharePoint Online для управления пользователями в среде SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7ef11-p119">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="7ef11-180">См. также</span><span class="sxs-lookup"><span data-stu-id="7ef11-180">See also</span></span>

[<span data-ttu-id="7ef11-181">Подключение к SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ef11-181">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="7ef11-182">Управление SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ef11-182">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="7ef11-183">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="7ef11-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="7ef11-184">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ef11-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

