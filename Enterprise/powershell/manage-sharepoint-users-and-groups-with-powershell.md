---
title: Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell
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
description: 'Сводка: Использование Office 365 PowerShell для управления SharePoint Online пользователями, группами и сайтами.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="9a22b-103">Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a22b-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="9a22b-104">**Сводка:** Использование Office 365 PowerShell для управления SharePoint Online пользователей, групп и сайтов.</span><span class="sxs-lookup"><span data-stu-id="9a22b-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="9a22b-105">Если вы являетесь SharePoint Online, для работы с большими списками учетных записей пользователей или групп, а также выполнить более простой способ управления ими, можно использовать Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a22b-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="9a22b-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="9a22b-106">Before you begin</span></span>

<span data-ttu-id="9a22b-p101">Процедуры, описанные в этом разделе требуется подключение к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="9a22b-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="9a22b-109">Получение списков сайтов, групп и пользователей</span><span class="sxs-lookup"><span data-stu-id="9a22b-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="9a22b-p102">Прежде чем мы начнем управлять пользователями и группами, вам необходимо получить список сайтов, групп и пользователей. Эту информацию можно использовать для работы с примером в данной статье.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="9a22b-112">Получение списка сайтов</span><span class="sxs-lookup"><span data-stu-id="9a22b-112">Get a list of sites</span></span>

<span data-ttu-id="9a22b-113">Чтобы получить список сайтов в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9a22b-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="9a22b-114">Получение списка групп</span><span class="sxs-lookup"><span data-stu-id="9a22b-114">Get a list of groups</span></span>

<span data-ttu-id="9a22b-115">Чтобы получить список групп в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9a22b-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="9a22b-116">Получение списка пользователей</span><span class="sxs-lookup"><span data-stu-id="9a22b-116">Get a list of users</span></span>

<span data-ttu-id="9a22b-117">Чтобы получить список пользователей в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9a22b-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="9a22b-118">Добавление пользователя в группу администраторов семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="9a22b-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="9a22b-p103">Команда **Set-SPOUser** для добавления пользователя в список администраторов семейства сайтов в семействе сайтов. Это, как будет выглядеть следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="9a22b-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="9a22b-121">В этом примере использует переменные для хранения значения и имеет заметки в сценарии (например "<!--This is the Tenant Name…-->«) для лучшего понимания эти значения, которые должны быть.</span><span class="sxs-lookup"><span data-stu-id="9a22b-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="9a22b-122">К примеру этот набор команд добавляет Opal Castillo (opalc имени пользователя) список Администраторы семейства сайтов в семействе сайтов ContosoTest в клиенте contoso1:</span><span class="sxs-lookup"><span data-stu-id="9a22b-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="9a22b-123">Вы можете скопировать и вставить эти команды в Блокноте, изменить значения перемененных $tenant, $site и $user на фактические значения из вашей среды, а затем вставить полученную команду в окно командной консоли SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9a22b-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="9a22b-124">Добавление пользователя в другие группы администраторов семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="9a22b-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="9a22b-p104">В этой задаче будет использовать команду **Add-SPOUser** для добавления пользователя в группу SharePoint в семействе сайтов. Это, как будет выглядеть следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="9a22b-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="9a22b-127">Например добавим Rife Glen (glenr имени пользователя) группе аудиторов на семейства сайтов ContosoTest в клиенте contoso1:</span><span class="sxs-lookup"><span data-stu-id="9a22b-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="9a22b-128">Создание группы семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="9a22b-128">Create a site collection group</span></span>

<span data-ttu-id="9a22b-p105">Команда **Set-SPOSiteGroup** используется для создания новой группы SharePoint и добавить его в семейство сайтов ContosoTest. Это, как будет выглядеть следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="9a22b-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> <span data-ttu-id="9a22b-p106">Любая строка с пробелами необходимо заключить в кавычки. Группируйте свойства, такие как уровни разрешений можно было обновить с помощью командлета **Set-SPOSiteGroup** .</span><span class="sxs-lookup"><span data-stu-id="9a22b-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="9a22b-133">Например добавим аудиторы группы с разрешениями только просмотр Contoso тестовых семейства веб-сайтов в клиенте contoso1:</span><span class="sxs-lookup"><span data-stu-id="9a22b-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="9a22b-134">Удаление пользователей из группы</span><span class="sxs-lookup"><span data-stu-id="9a22b-134">Remove users from a group</span></span>

<span data-ttu-id="9a22b-p107">Иногда необходимо удалить пользователя с сайта или даже со всех сайтов. Возможно, сотрудник переводится из одного подразделения в другое или увольняется из компании. Одного сотрудника можно легко удалить в пользовательском интерфейсе, однако не так-то просто перенести целое подразделение с одного сайта на другой.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="9a22b-p108">Однако с помощью файлов Командная консоль SharePoint Online и CSV, это легко и быстро. В этой задаче будет использовать Windows PowerShell для удаления пользователя из группы безопасности семейства сайтов. Затем можно использовать в CSV-файл и удаление большое количество пользователей на различных сайтах.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="9a22b-p109">Мы будем использование команды **Remove-SPOUser** для удаления отдельному пользователю Office 365 из группы семейства сайтов только в том случае, поэтому можно увидеть синтаксис команды. В этом разделе представлен следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="9a22b-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

<span data-ttu-id="9a22b-143">Например давайте удалить Bobby Overby из группы аудиторов семейства сайтов в семействе сайтов тестирования Contoso в клиенте contoso1:</span><span class="sxs-lookup"><span data-stu-id="9a22b-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="9a22b-p110">Предположим, что мы хотим удалить Bobby из всех групп, в которых он состоит. Вот как это сделать:</span><span class="sxs-lookup"><span data-stu-id="9a22b-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="9a22b-p111">Это просто пример, как это можно сделать. Не следует выполнять эту команду, если вам действительно не требуется удалить пользователя из каждой группы, например если пользователь уволится из компании.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="9a22b-148">Автоматизация управления большими списками пользователей и групп</span><span class="sxs-lookup"><span data-stu-id="9a22b-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="9a22b-p112">Чтобы добавить большое число учетных записей для сайтов SharePoint и предоставьте им разрешения, можно использовать Центр администрирования Office 365, отдельные команды PowerShell или PowerShell в CSV-файл. Эти варианты выбора CSV-файл является быстрым способом для автоматизации этой задачи.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="9a22b-p113">Базовый процесс заключается в создании CSV-файл, который есть заголовки (столбцы), которые соответствуют параметрам, которые должен сценарий Windows PowerShell. Можно легко создавать такой список в Excel и его экспорта в CSV-файл. Затем используйте сценарий Windows PowerShell для итерации записей (строк) в CSV-файл, добавление пользователей в группы и группы к сайтам.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="9a22b-p114">Для примера создадим CSV-файл, чтобы определить группу семейств сайтов, групп и разрешений. Затем мы создадим CSV-файл, чтобы заполнить группы пользователями. Наконец, мы создадим и выполним простой скрипт Windows PowerShell, который создает и заполняет группы.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="9a22b-157">Первый CSV-файл добавляет одну или несколько групп в одно или несколько семейств сайтов. Он использует следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="9a22b-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="9a22b-158">Заголовок:</span><span class="sxs-lookup"><span data-stu-id="9a22b-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="9a22b-159">Элемент:</span><span class="sxs-lookup"><span data-stu-id="9a22b-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="9a22b-160">Ниже приведен пример файла:</span><span class="sxs-lookup"><span data-stu-id="9a22b-160">Here is an example file:</span></span>

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

<span data-ttu-id="9a22b-161">Второй CSV-файл добавляет одного или нескольких пользователей в одну или несколько групп. Он использует следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="9a22b-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="9a22b-162">Заголовок:</span><span class="sxs-lookup"><span data-stu-id="9a22b-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="9a22b-163">Элемент:</span><span class="sxs-lookup"><span data-stu-id="9a22b-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="9a22b-164">Ниже приведен пример файла:</span><span class="sxs-lookup"><span data-stu-id="9a22b-164">Here is an example file:</span></span>

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

<span data-ttu-id="9a22b-p115">Затем необходимо сохранить на диск два CSV-файла. Ниже перечислены команды, которые используют оба CSV-файла, а также применяются для добавления разрешений и членства в группах.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="9a22b-p116">Сценарий импортирует содержимое файла CSV и использует значения в столбцах (полужирным шрифтом) для заполнения параметров команды **New-SPOSiteGroup** и **Add-SPOUser** . В нашем примере мы сохранение на диске C, но его можно сохранить там, где хотите.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="9a22b-p117">Удалим множество пользователей из нескольких групп на различных сайтах с помощью этого же CSV-файла. Вот необходимая для этого команда:</span><span class="sxs-lookup"><span data-stu-id="9a22b-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="9a22b-171">Создание отчетов о пользователях</span><span class="sxs-lookup"><span data-stu-id="9a22b-171">Generate user reports</span></span>

<span data-ttu-id="9a22b-p118">Возможно, вам потребуется простой отчет о пользователях нескольких сайтов, их уровне разрешений и других свойствах. Вот как выглядит синтаксис команды:</span><span class="sxs-lookup"><span data-stu-id="9a22b-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="9a22b-p119">Это взять данные для этих трех сайтов и записать их в текстовый файл на локальном диске. Обратите внимание, что параметр – Append будет добавления нового контента в существующий файл.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="9a22b-176">Например, запустим отчет на сайтах ContosoTest, TeamSite01 и Project01 клиентской организации Contoso1.</span><span class="sxs-lookup"><span data-stu-id="9a22b-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="9a22b-p120">Обратите внимание, что у нас изменение только переменной **$site** . Переменная **$tenant** сохраняет свое значение через все три выполнения команды.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="9a22b-p121">Но что делать, если вы хотите сделать это для каждого сайта? Используйте эту команду, чтобы не вводить все нужные веб-сайты:</span><span class="sxs-lookup"><span data-stu-id="9a22b-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="9a22b-p122">В этом отчете довольно прост, и можно добавить дополнительный код для создания более подробные отчеты или отчеты, содержащие более подробные сведения. Однако это должно дать о том, как использовать командную консоль SharePoint Online для управления пользователями в среде SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9a22b-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="9a22b-183">См. также</span><span class="sxs-lookup"><span data-stu-id="9a22b-183">See also</span></span>

[<span data-ttu-id="9a22b-184">Подключение к SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a22b-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="9a22b-185">Управление SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a22b-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="9a22b-186">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="9a22b-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9a22b-187">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a22b-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

