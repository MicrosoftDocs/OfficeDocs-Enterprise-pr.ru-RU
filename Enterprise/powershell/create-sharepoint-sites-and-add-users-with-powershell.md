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
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="f26b3-103">Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f26b3-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

<span data-ttu-id="f26b3-104">Когда вы используете Office 365 PowerShell для создания сайтов SharePoint Online и добавления пользователей, вы можете быстро и многократно выполнять задачи гораздо быстрее, чем в центре администрирования Майкрософт 365.</span><span class="sxs-lookup"><span data-stu-id="f26b3-104">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Microsoft 365 admin center.</span></span> <span data-ttu-id="f26b3-105">Вы также можете выполнять задачи, которые невозможно выполнить в центре администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="f26b3-105">You can also perform tasks that are not possible to perform in the Office 365 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="f26b3-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="f26b3-106">Before you begin</span></span>

<span data-ttu-id="f26b3-107">Процедуры, описанные в этом разделе, требуют подключения к SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f26b3-107">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="f26b3-108">Инструкции см в разделе [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="f26b3-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="f26b3-109">Шаг 1. Создание семейств веб-сайтов с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f26b3-109">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="f26b3-110">Создайте несколько сайтов с помощью PowerShell для Office 365 и CSV-файла, созданного с помощью примера кода и блокнота.</span><span class="sxs-lookup"><span data-stu-id="f26b3-110">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="f26b3-111">В этой процедуре заменяются сведения о заполнителе, показанные в квадратных скобках, с собственными сведениями о сайтах и клиентах.</span><span class="sxs-lookup"><span data-stu-id="f26b3-111">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="f26b3-112">Этот процесс позволяет создать один файл и запустить одну команду PowerShell Office 365, использующую этот файл.</span><span class="sxs-lookup"><span data-stu-id="f26b3-112">This process lets you create a single file and run a single Office 365 PowerShell command that uses that file.</span></span> <span data-ttu-id="f26b3-113">Это делает действия, которые были как повторяющимися, так и переносимыми, и исключает многие, если не все, ошибки, которые могут возникнуть при вводе длинных команд в командную консоль SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f26b3-113">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="f26b3-114">Эта процедура состоит из двух частей.</span><span class="sxs-lookup"><span data-stu-id="f26b3-114">There are two parts to this procedure.</span></span> <span data-ttu-id="f26b3-115">Сначала вы создадите CSV-файл, а затем сослаться на этот CSV-файл с помощью Office 365 PowerShell, который будет использовать его содержимое для создания сайтов.</span><span class="sxs-lookup"><span data-stu-id="f26b3-115">First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="f26b3-116">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers.</span><span class="sxs-lookup"><span data-stu-id="f26b3-116">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers.</span></span> <span data-ttu-id="f26b3-117">The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span><span class="sxs-lookup"><span data-stu-id="f26b3-117">The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="f26b3-118">Создание CSV-файла</span><span class="sxs-lookup"><span data-stu-id="f26b3-118">Create a .csv file</span></span>

1. <span data-ttu-id="f26b3-119">Откройте Блокнот и вставьте в него следующий блок текста:</span><span class="sxs-lookup"><span data-stu-id="f26b3-119">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="f26b3-120">Где *клиент* — это имя вашего клиента, а *owner* — это имя пользователя в клиенте, которому требуется предоставить роль главного администратора семейства веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="f26b3-120">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="f26b3-121">(Можно нажать клавиши CTRL + H при использовании блокнота для ускорения массового замещения.)</span><span class="sxs-lookup"><span data-stu-id="f26b3-121">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="f26b3-122">Сохраните файл на рабочем столе как **SiteCollections.csv**.</span><span class="sxs-lookup"><span data-stu-id="f26b3-122">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="f26b3-123">Перед использованием этого или другого файла сценария. CSV или Windows PowerShell рекомендуется убедиться в отсутствии лишних или непечатаемых символов.</span><span class="sxs-lookup"><span data-stu-id="f26b3-123">Before you use this or any other .csv or Windows PowerShell script file, it's a good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="f26b3-124">Откройте файл в Word и щелкните значок абзаца на ленте, чтобы показать непечатаемые символы.</span><span class="sxs-lookup"><span data-stu-id="f26b3-124">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="f26b3-125">Файлы не должны содержать лишние непечатаемые символы.</span><span class="sxs-lookup"><span data-stu-id="f26b3-125">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="f26b3-126">Например, в конце файла не должно быть знаков абзаца.</span><span class="sxs-lookup"><span data-stu-id="f26b3-126">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="f26b3-127">Выполнение команды Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f26b3-127">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="f26b3-128">В командной консоли Windows PowerShell введите (или скопируйте и вставьте) следующую команду и нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="f26b3-128">At the Windows PowerShell prompt, type or copy and paste the following command, and press Enter:</span></span><br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="f26b3-129">Где *мялиас* соответствует псевдониму пользователя.</span><span class="sxs-lookup"><span data-stu-id="f26b3-129">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="f26b3-130">Wait for the Windows PowerShell prompt to reappear.</span><span class="sxs-lookup"><span data-stu-id="f26b3-130">Wait for the Windows PowerShell prompt to reappear.</span></span> <span data-ttu-id="f26b3-131">It might take a minute or two.</span><span class="sxs-lookup"><span data-stu-id="f26b3-131">It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="f26b3-132">В командной строке Windows PowerShell введите или скопируйте и вставьте следующий командлет, а затем нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="f26b3-132">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="f26b3-133">Обратите внимание на новые семейства веб-сайтов в списке.</span><span class="sxs-lookup"><span data-stu-id="f26b3-133">Note the new site collections in the list.</span></span> <span data-ttu-id="f26b3-134">Используя наш пример CSV-файла, вы увидите следующие семейства веб-сайтов: **TeamSite01**, **Blog01**, **Project01**и **Community01**</span><span class="sxs-lookup"><span data-stu-id="f26b3-134">Using our example CSV file, you would see the following site collections: **TeamSite01**, **Blog01**, **Project01**, and **Community01**</span></span>

<span data-ttu-id="f26b3-135">Вот и все.</span><span class="sxs-lookup"><span data-stu-id="f26b3-135">That’s it.</span></span> <span data-ttu-id="f26b3-136">Вы создали несколько семейств веб-сайтов с помощью созданного CSV-файла и одной команды Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f26b3-136">You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell command.</span></span> <span data-ttu-id="f26b3-137">Теперь вы можете создать пользователей и назначить их сайтам.</span><span class="sxs-lookup"><span data-stu-id="f26b3-137">You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="f26b3-138">Действие 2. Добавление пользователей или групп</span><span class="sxs-lookup"><span data-stu-id="f26b3-138">Step 2: Add users and groups</span></span>

<span data-ttu-id="f26b3-139">Now you’re going to create users and add them to a site collection group.</span><span class="sxs-lookup"><span data-stu-id="f26b3-139">Now you’re going to create users and add them to a site collection group.</span></span> <span data-ttu-id="f26b3-140">You will then use a .csv file to bulk upload new groups and users.</span><span class="sxs-lookup"><span data-stu-id="f26b3-140">You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="f26b3-141">Следующие процедуры продолжают использовать примеры сайтов TeamSite01, Blog01, Project01 и Community01.</span><span class="sxs-lookup"><span data-stu-id="f26b3-141">The following procedures continue using the example sites TeamSite01, Blog01, Project01, and Community01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="f26b3-142">Создание CSV- и PS1-файлов</span><span class="sxs-lookup"><span data-stu-id="f26b3-142">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="f26b3-143">Откройте Блокнот и вставьте в него следующий блок текста:</span><span class="sxs-lookup"><span data-stu-id="f26b3-143">Open Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="f26b3-144">Где *клиент* равняется имени клиента.</span><span class="sxs-lookup"><span data-stu-id="f26b3-144">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="f26b3-145">Сохраните файл на рабочем столе как **GroupsAndPermissions.csv**.</span><span class="sxs-lookup"><span data-stu-id="f26b3-145">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="f26b3-146">Откройте новый экземпляр Блокнота и вставьте в него следующий блок текста:</span><span class="sxs-lookup"><span data-stu-id="f26b3-146">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="f26b3-147">Где *клиент* равняется имени клиента, а *username* — имя пользователя существующего пользователя.</span><span class="sxs-lookup"><span data-stu-id="f26b3-147">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="f26b3-148">Сохраните файл на рабочем столе как **Users.csv**.</span><span class="sxs-lookup"><span data-stu-id="f26b3-148">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="f26b3-149">Откройте новый экземпляр Блокнота и вставьте в него следующий блок текста:</span><span class="sxs-lookup"><span data-stu-id="f26b3-149">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="f26b3-150">Где Мялиас = имя пользователя, выполнившего вход в систему.</span><span class="sxs-lookup"><span data-stu-id="f26b3-150">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="f26b3-151">Сохраните файл на рабочем столе как **UsersAndGroups.ps1**.</span><span class="sxs-lookup"><span data-stu-id="f26b3-151">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="f26b3-152">Это простой сценарий Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f26b3-152">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="f26b3-153">Теперь вы можете выполнить скрипт UsersAndGroup.ps1, чтобы добавить пользователей и группы в несколько семейств сайтов.</span><span class="sxs-lookup"><span data-stu-id="f26b3-153">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="f26b3-154">Выполнение скрипта UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="f26b3-154">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="f26b3-155">Вернитесь в командную консоль SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f26b3-155">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="f26b3-156">В командной строке Windows PowerShell введите или скопируйте и вставьте следующую строку, а затем нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="f26b3-156">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="f26b3-157">В запросе подтверждения нажмите **Y**.</span><span class="sxs-lookup"><span data-stu-id="f26b3-157">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="f26b3-158">В командной строке Windows PowerShell введите и или скопируйте и вставьте следующую строку, а затем нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="f26b3-158">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="f26b3-159">Где *мялиас* = ваше имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="f26b3-159">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="f26b3-160">Wait for the prompt to return before moving on.</span><span class="sxs-lookup"><span data-stu-id="f26b3-160">Wait for the prompt to return before moving on.</span></span> <span data-ttu-id="f26b3-161">You will first see the groups appear as they are created.</span><span class="sxs-lookup"><span data-stu-id="f26b3-161">You will first see the groups appear as they are created.</span></span> <span data-ttu-id="f26b3-162">Then you will see the group list repeated as users are added.</span><span class="sxs-lookup"><span data-stu-id="f26b3-162">Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="f26b3-163">См. также</span><span class="sxs-lookup"><span data-stu-id="f26b3-163">See also</span></span>

[<span data-ttu-id="f26b3-164">Подключение к PowerShell в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f26b3-164">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="f26b3-165">Управление группами сайтов SharePoint Online в Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f26b3-165">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="f26b3-166">Управление Office 365 с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f26b3-166">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f26b3-167">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f26b3-167">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

