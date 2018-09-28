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
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="7f049-103">Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f049-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="7f049-104">**Сводка:** Для создания новых сайтов SharePoint Online с помощью Office 365 PowerShell, а затем добавьте пользователей и групп для этих сайтов.</span><span class="sxs-lookup"><span data-stu-id="7f049-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="7f049-p101">При использовании Office 365 PowerShell для создания сайтов SharePoint Online и добавление пользователей можно быстро и повторно выполнить задачи значительно быстрее, чем в центре администрирования Office 356. Можно также выполнять задачи, которые невозможно выполнить в центре администрирования Office 356.</span><span class="sxs-lookup"><span data-stu-id="7f049-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="7f049-107">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="7f049-107">Before you begin</span></span>

<span data-ttu-id="7f049-p102">Процедуры, описанные в этом разделе требуется подключение к SharePoint Online. Сведения содержатся в разделе [подключение к SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="7f049-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="7f049-110">Шаг 1. Создание семейств веб-сайтов с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f049-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="7f049-p103">Создайте несколько сайтов с помощью Office 365 PowerShell и CSV-файла. Чтобы создать CSV-файл, используйте пример кода и "Блокнот". Для этого необходимо заменить содержимое заполнителей в угловых скобках на данные о сайтах и клиенте. Эта процедура позволяет создать один файл и выполнить одну команду Office 365 PowerShell, которая использует этот файл. Благодаря этому действия можно повторять в разных средах, а также устраняются многие, если не все, ошибки, связанные с вводом длинных команд в командной консоли SharePoint Online. Эта процедура состоит из двух частей. Сначала вы создаете CSV-файл, а затем ссылаетесь на него с помощью Office 365 PowerShell. Содержимое файла будет использоваться для создания сайтов.</span><span class="sxs-lookup"><span data-stu-id="7f049-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process allows you to create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="7f049-p104">Командлет Office 365 PowerShell импортирует CSV-файл и передает его в цикл в фигурных скобках, который считывает первую строку файла как заголовки столбцов. Командлет Office 365 PowerShell проходит по остальным записям, создает семейство веб-сайтов для каждой из них и назначает свойства семейства веб-сайтов в соответствии с заголовками столбцов.</span><span class="sxs-lookup"><span data-stu-id="7f049-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="7f049-119">Создание CSV-файла</span><span class="sxs-lookup"><span data-stu-id="7f049-119">Create a .csv file</span></span>

1. <span data-ttu-id="7f049-120">Откройте Блокнот и вставьте в него следующий блок текста:</span><span class="sxs-lookup"><span data-stu-id="7f049-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="7f049-121">Где *клиента* — это имя клиента, а *владелец* — это имя пользователя в клиенте, которому необходимо предоставить роль основного администратора семейства сайтов.</span><span class="sxs-lookup"><span data-stu-id="7f049-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="7f049-122">(Клавиши Ctrl + H может, при использовании "Блокнот" для массового заменить быстрее.)</span><span class="sxs-lookup"><span data-stu-id="7f049-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="7f049-123">Сохраните файл на рабочем столе как **SiteCollections.csv**.</span><span class="sxs-lookup"><span data-stu-id="7f049-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="7f049-p105">Прежде чем использовать это или любой другой .csv или файл сценария Windows PowerShell, рекомендуется убедитесь в том, что не используются никакие лишние или непечатаемые символы. Откройте файл Word и на ленте, щелкните значок абзаца, чтобы показать непечатаемые символы. Должно быть не лишние непечатаемых знаков. Например должно быть не служебные знаки за последний один в конце файла.</span><span class="sxs-lookup"><span data-stu-id="7f049-p105">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="7f049-128">Выполнение команды Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f049-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="7f049-129">В командной строке Windows PowerShell введите или скопируйте и вставьте следующий командлет, а затем нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="7f049-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="7f049-130">Где *MyAlias* — это псевдоним пользователя.</span><span class="sxs-lookup"><span data-stu-id="7f049-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="7f049-p106">Дождитесь появления окна командной строки Windows PowerShell. Для этого может потребоваться одна или две минуты.</span><span class="sxs-lookup"><span data-stu-id="7f049-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="7f049-133">В командной строке Windows PowerShell введите или скопируйте и вставьте следующий командлет, а затем нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="7f049-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="7f049-p107">Обратите внимание, новых семейств сайтов в списке. Должно появиться следующие семейства сайтов: **сайтов contosotest**, **TeamSite01**, **Blog01**и **Project01**</span><span class="sxs-lookup"><span data-stu-id="7f049-p107">Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="7f049-p108">Вот и все. Вы создали несколько семейств веб-сайтов с помощью CSV-файла и одного командлета Windows PowerShell. Теперь вы можете создать пользователей и назначить их сайтам.</span><span class="sxs-lookup"><span data-stu-id="7f049-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="7f049-139">Действие 2. Добавление пользователей или групп</span><span class="sxs-lookup"><span data-stu-id="7f049-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="7f049-p109">Теперь мы создадим пользователей и добавим их в группу семейства сайтов. Мы используем CSV-файл для массовой загрузки новых групп и пользователей.</span><span class="sxs-lookup"><span data-stu-id="7f049-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="7f049-142">В следующих процедурах предполагается, что вы успешно создали семейства сайтов contosotest, TeamSite01, Blog01 и Project01.</span><span class="sxs-lookup"><span data-stu-id="7f049-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="7f049-143">Создание CSV- и PS1-файлов</span><span class="sxs-lookup"><span data-stu-id="7f049-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="7f049-144">Откройте Блокнот и вставьте в него следующий блок текста:</span><span class="sxs-lookup"><span data-stu-id="7f049-144">Open Notepad, and paste the following text block into it:</span></span><br/>
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
<br/><span data-ttu-id="7f049-145">Где *клиента* — это имя клиента.</span><span class="sxs-lookup"><span data-stu-id="7f049-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="7f049-146">Сохраните файл на рабочем столе как **GroupsAndPermissions.csv**.</span><span class="sxs-lookup"><span data-stu-id="7f049-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="7f049-147">Откройте новый экземпляр Блокнота и вставьте в него следующий блок текста:</span><span class="sxs-lookup"><span data-stu-id="7f049-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="7f049-148">Где *клиента* — это имя клиента, а *имя пользователя* — имя существующего пользователя.</span><span class="sxs-lookup"><span data-stu-id="7f049-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="7f049-149">Сохраните файл на рабочем столе именем **Users.csv**.</span><span class="sxs-lookup"><span data-stu-id="7f049-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="7f049-150">Откройте новый экземпляр Блокнота и вставьте в него следующий блок текста:</span><span class="sxs-lookup"><span data-stu-id="7f049-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="7f049-151">Где MyAlias — имя пользователя, вошедшего в систему.</span><span class="sxs-lookup"><span data-stu-id="7f049-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="7f049-p110">Сохраните файл на рабочем столе как **UsersAndGroups.ps1**. Это простое сценария Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f049-p110">Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="7f049-154">Теперь вы можете выполнить скрипт UsersAndGroup.ps1, чтобы добавить пользователей и группы в несколько семейств сайтов.</span><span class="sxs-lookup"><span data-stu-id="7f049-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="7f049-155">Выполнение скрипта UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="7f049-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="7f049-156">Вернитесь в командную консоль SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7f049-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="7f049-157">В командной строке Windows PowerShell введите или скопируйте и вставьте следующую строку, а затем нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="7f049-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="7f049-158">В окне подтверждения нажмите клавишу **Y**.</span><span class="sxs-lookup"><span data-stu-id="7f049-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="7f049-159">В командной строке Windows PowerShell введите и или скопируйте и вставьте следующую строку, а затем нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="7f049-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="7f049-160">Где *MyAlias* — это имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="7f049-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="7f049-p111">Дождитесь появления окна командной строки. Сначала вы увидите группы по мере их создания. Затем вы увидите список групп, который повторяется при добавлении пользователей.</span><span class="sxs-lookup"><span data-stu-id="7f049-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f049-164">См. также</span><span class="sxs-lookup"><span data-stu-id="7f049-164">See also</span></span>

[<span data-ttu-id="7f049-165">Подключение к PowerShell в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7f049-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="7f049-166">Управление группами SharePoint Online сайт Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f049-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="7f049-167">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="7f049-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="7f049-168">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f049-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

