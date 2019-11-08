---
title: Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Сводка: использование PowerShell для Office 365 для управления пользователями, группами и сайтами SharePoint Online.'
ms.openlocfilehash: 8133af978e2a63bf18b825ca6b6bdb430e676b72
ms.sourcegitcommit: b4514cd852093181dd4c27009a78aca3ca50d2e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "38038228"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="2f29e-103">Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f29e-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="2f29e-104">**Сводка:** Используйте Office 365 PowerShell для управления пользователями, группами и сайтами SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="2f29e-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="2f29e-105">Если вы являетесь администратором SharePoint Online, который работает с большими списками учетных записей пользователей или групп и хотите упростить управление ими, вы можете использовать PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="2f29e-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="2f29e-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="2f29e-106">Before you begin</span></span>

<span data-ttu-id="2f29e-107">Процедуры, описанные в этом разделе, требуют подключения к SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="2f29e-107">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="2f29e-108">Инструкции см в разделе [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="2f29e-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="2f29e-109">Получение списков сайтов, групп и пользователей</span><span class="sxs-lookup"><span data-stu-id="2f29e-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="2f29e-p102">Прежде чем мы начнем управлять пользователями и группами, вам необходимо получить список сайтов, групп и пользователей. Эту информацию можно использовать для работы с примером в данной статье.</span><span class="sxs-lookup"><span data-stu-id="2f29e-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="2f29e-112">Получение списка сайтов</span><span class="sxs-lookup"><span data-stu-id="2f29e-112">Get a list of sites</span></span>

<span data-ttu-id="2f29e-113">Чтобы получить список сайтов в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f29e-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="2f29e-114">Получение списка групп</span><span class="sxs-lookup"><span data-stu-id="2f29e-114">Get a list of groups</span></span>

<span data-ttu-id="2f29e-115">Чтобы получить список групп в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f29e-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="2f29e-116">Получение списка пользователей</span><span class="sxs-lookup"><span data-stu-id="2f29e-116">Get a list of users</span></span>

<span data-ttu-id="2f29e-117">Чтобы получить список пользователей в своем клиенте, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f29e-117">Get a list of the users in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="2f29e-118">Добавление пользователя в группу администраторов семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="2f29e-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="2f29e-119">Используйте команду **Set-SPOUser**, чтобы добавить пользователя в список администраторов семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="2f29e-119">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection.</span></span> <span data-ttu-id="2f29e-120">Вот как выглядит синтаксис команды:</span><span class="sxs-lookup"><span data-stu-id="2f29e-120">This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="2f29e-121">Чтобы использовать эти команды, замените "заменить все" в кавычках, включая < и > символы, указав правильные имена.</span><span class="sxs-lookup"><span data-stu-id="2f29e-121">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="2f29e-122">Например, этот набор команд добавляет Кастилло Opalis (имя пользователя opalc), список администраторов семейства веб-сайтов в семействе веб-сайтов ContosoTest в клиентской организации Contoso1:</span><span class="sxs-lookup"><span data-stu-id="2f29e-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="2f29e-123">Вы можете скопировать и вставить эти команды в блокнот, изменить значения переменных для $tenant, $site и $user на фактические значения из вашей среды, а затем вставить их в окно командной консоли SharePoint Online для их запуска.</span><span class="sxs-lookup"><span data-stu-id="2f29e-123">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-groups"></a><span data-ttu-id="2f29e-124">Добавление пользователя в другие группы семейств веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="2f29e-124">Add a user to other site collection groups</span></span>

<span data-ttu-id="2f29e-125">Для этой задачи мы используем команду **Add-SPOUser**, чтобы добавить пользователя в группу SharePoint в семействе сайтов.</span><span class="sxs-lookup"><span data-stu-id="2f29e-125">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="2f29e-126">Например, давайте добавим пользователя Glen Rife (с именем пользователя "glenr") в группу аудиторов в семействе веб-сайтов ContosoTest клиентской организации contoso1.</span><span class="sxs-lookup"><span data-stu-id="2f29e-126">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="2f29e-127">Создание группы семейства веб-сайтов</span><span class="sxs-lookup"><span data-stu-id="2f29e-127">Create a site collection group</span></span>

<span data-ttu-id="2f29e-128">Используйте команду **New-SPOSiteGroup** , чтобы создать новую группу SharePoint и добавить ее в семейство веб-сайтов ContosoTest.</span><span class="sxs-lookup"><span data-stu-id="2f29e-128">You use the **New-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="2f29e-129">Свойства группы, например уровни разрешений, можно обновить позднее с помощью командлета **Set-SPOSiteGroup**.</span><span class="sxs-lookup"><span data-stu-id="2f29e-129">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="2f29e-130">Например, добавим группу аудиторий с разрешениями только на просмотр для тестового семейства веб-сайтов Contoso в Contoso1.</span><span class="sxs-lookup"><span data-stu-id="2f29e-130">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="2f29e-131">Удаление пользователей из группы</span><span class="sxs-lookup"><span data-stu-id="2f29e-131">Remove users from a group</span></span>

<span data-ttu-id="2f29e-p104">Иногда необходимо удалить пользователя с сайта или даже со всех сайтов. Возможно, сотрудник переводится из одного подразделения в другое или увольняется из компании. Одного сотрудника можно легко удалить в пользовательском интерфейсе, однако не так-то просто перенести целое подразделение с одного сайта на другой.</span><span class="sxs-lookup"><span data-stu-id="2f29e-p104">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="2f29e-135">Однако с помощью командной консоли SharePoint Online и CSV-файлов это быстро и легко.</span><span class="sxs-lookup"><span data-stu-id="2f29e-135">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="2f29e-136">Для этой задачи вы используете Windows PowerShell, чтобы удалить пользователя из группы безопасности семейства сайтов.</span><span class="sxs-lookup"><span data-stu-id="2f29e-136">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="2f29e-137">Затем вы используете CSV-файл и удалите множество пользователей с разных сайтов.</span><span class="sxs-lookup"><span data-stu-id="2f29e-137">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="2f29e-138">Мы будем использовать команду **Remove-супруг** для удаления одного пользователя Office 365 из группы семейств веб-сайтов, так как мы можем увидеть синтаксис команды.</span><span class="sxs-lookup"><span data-stu-id="2f29e-138">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="2f29e-139">Вот как выглядит синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2f29e-139">Here is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="2f29e-140">Например, давайте удалим Бобби Оверби из группы аудиторий семейства веб-сайтов в тестовом семействе веб-сайтов Contoso в клиенте Contoso1:</span><span class="sxs-lookup"><span data-stu-id="2f29e-140">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="2f29e-141">Предположим, что мы хотим удалить Bobby из всех групп, в которых он состоит.</span><span class="sxs-lookup"><span data-stu-id="2f29e-141">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="2f29e-142">Вот как это сделать:</span><span class="sxs-lookup"><span data-stu-id="2f29e-142">Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="2f29e-143">Это всего лишь пример.</span><span class="sxs-lookup"><span data-stu-id="2f29e-143">This is just an example.</span></span> <span data-ttu-id="2f29e-144">Не следует выполнять эту команду, если вам действительно не требуется удалить пользователя из каждой группы, например если пользователь уволится из компании.</span><span class="sxs-lookup"><span data-stu-id="2f29e-144">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="2f29e-145">Автоматизация управления большими списками пользователей и групп</span><span class="sxs-lookup"><span data-stu-id="2f29e-145">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="2f29e-146">Для добавления большого количества учетных записей на сайты SharePoint и предоставления им разрешений можно использовать центр администрирования Microsoft 365, отдельные команды PowerShell или файл CSV.</span><span class="sxs-lookup"><span data-stu-id="2f29e-146">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="2f29e-147">Быстрее всего эту задачу можно автоматизировать с помощью CSV-файла.</span><span class="sxs-lookup"><span data-stu-id="2f29e-147">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="2f29e-148">Создайте CSV-файл с заголовками (столбцами), соответствующими параметрам скрипта Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f29e-148">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="2f29e-149">Такой список можно легко создать в Excel, а затем экспортировать в виде CSV-файла.</span><span class="sxs-lookup"><span data-stu-id="2f29e-149">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="2f29e-150">Затем с помощью скрипта Windows PowerShell вы пройдете по всем записям (строкам) в CSV-файле, добавляя пользователей в группы и группы в сайты.</span><span class="sxs-lookup"><span data-stu-id="2f29e-150">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="2f29e-p111">Для примера создадим CSV-файл, чтобы определить группу семейств сайтов, групп и разрешений. Затем мы создадим CSV-файл, чтобы заполнить группы пользователями. Наконец, мы создадим и выполним простой скрипт Windows PowerShell, который создает и заполняет группы.</span><span class="sxs-lookup"><span data-stu-id="2f29e-p111">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="2f29e-154">Первый CSV-файл добавляет одну или несколько групп в одно или несколько семейств сайтов. Он использует следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="2f29e-154">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="2f29e-155">Верхний</span><span class="sxs-lookup"><span data-stu-id="2f29e-155">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="2f29e-156">Элемента</span><span class="sxs-lookup"><span data-stu-id="2f29e-156">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="2f29e-157">Ниже приведен пример файла:</span><span class="sxs-lookup"><span data-stu-id="2f29e-157">Here is an example file:</span></span>

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

<span data-ttu-id="2f29e-158">Второй CSV-файл добавляет одного или нескольких пользователей в одну или несколько групп. Он использует следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="2f29e-158">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="2f29e-159">Верхний</span><span class="sxs-lookup"><span data-stu-id="2f29e-159">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="2f29e-160">Элемента</span><span class="sxs-lookup"><span data-stu-id="2f29e-160">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="2f29e-161">Ниже приведен пример файла:</span><span class="sxs-lookup"><span data-stu-id="2f29e-161">Here is an example file:</span></span>

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

<span data-ttu-id="2f29e-162">Затем необходимо сохранить на диск два CSV-файла.</span><span class="sxs-lookup"><span data-stu-id="2f29e-162">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="2f29e-163">Ниже приведены примеры команд, использующих как CSV-файлы, так и добавления разрешений и членства в группах.</span><span class="sxs-lookup"><span data-stu-id="2f29e-163">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="2f29e-164">Сценарий импортирует содержимое CSV-файла и использует значения в столбцах для заполнения параметров команд **New-SPOSiteGroup** и **Add-супруг** .</span><span class="sxs-lookup"><span data-stu-id="2f29e-164">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="2f29e-165">В нашем примере мы сохраняем это в папке theO365Admin на диске C, но вы можете сохранить ее там, где бы вы ни находились.</span><span class="sxs-lookup"><span data-stu-id="2f29e-165">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="2f29e-166">Удалим множество пользователей из нескольких групп на различных сайтах с помощью этого же CSV-файла.</span><span class="sxs-lookup"><span data-stu-id="2f29e-166">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="2f29e-167">Вот пример необходимой команды:</span><span class="sxs-lookup"><span data-stu-id="2f29e-167">Here is an example command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="2f29e-168">Создание отчетов о пользователях</span><span class="sxs-lookup"><span data-stu-id="2f29e-168">Generate user reports</span></span>

<span data-ttu-id="2f29e-p115">Возможно, вам потребуется простой отчет о пользователях нескольких сайтов, их уровне разрешений и других свойствах. Вот как выглядит синтаксис команды:</span><span class="sxs-lookup"><span data-stu-id="2f29e-p115">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="2f29e-171">Команда получает данные для этих трех сайтов и записывает их в текстовый файл на локальном диске.</span><span class="sxs-lookup"><span data-stu-id="2f29e-171">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="2f29e-172">Обратите внимание, что параметр –Append добавляет новый контент в существующий файл.</span><span class="sxs-lookup"><span data-stu-id="2f29e-172">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="2f29e-173">Например, запустим отчет на сайтах ContosoTest, TeamSite01 и Project01 клиентской организации Contoso1.</span><span class="sxs-lookup"><span data-stu-id="2f29e-173">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="2f29e-174">Обратите внимание, что нам пришлось изменить только переменную **$site** .</span><span class="sxs-lookup"><span data-stu-id="2f29e-174">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="2f29e-175">Переменная **$tenant** сохраняет свое значение по всем трем запускам команды.</span><span class="sxs-lookup"><span data-stu-id="2f29e-175">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="2f29e-p118">Но что делать, если вы хотите сделать это для каждого сайта? Используйте эту команду, чтобы не вводить все нужные веб-сайты:</span><span class="sxs-lookup"><span data-stu-id="2f29e-p118">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="2f29e-178">Это довольно простой отчет, и вы можете добавить код, чтобы создать более сложные отчеты или отчеты с более подробной информацией.</span><span class="sxs-lookup"><span data-stu-id="2f29e-178">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="2f29e-179">Однако в этом случае необходимо понять, как использовать командную консоль SharePoint Online для управления пользователями в среде SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="2f29e-179">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="2f29e-180">См. также</span><span class="sxs-lookup"><span data-stu-id="2f29e-180">See also</span></span>

[<span data-ttu-id="2f29e-181">Подключение к PowerShell в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2f29e-181">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="2f29e-182">Управление SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f29e-182">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="2f29e-183">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="2f29e-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2f29e-184">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f29e-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

