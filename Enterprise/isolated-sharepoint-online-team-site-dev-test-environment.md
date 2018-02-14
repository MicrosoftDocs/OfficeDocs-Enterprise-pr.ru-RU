---
title: "Изолированный SharePoint Online группы сайта dev/тестовой среды"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: "Сводка: Настройка сайта группы SharePoint Online, изолируется от других отделов организации в среде разработки и тестирования Office 365."
ms.openlocfilehash: c6115e48f1b2453aaf173b384a30c1cc34ce7b5a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a><span data-ttu-id="96eb1-103">Изолированный SharePoint Online группы сайта dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="96eb1-103">Isolated SharePoint Online team site dev/test environment</span></span>

 <span data-ttu-id="96eb1-104">**Сводка:** Настройка сайта группы SharePoint Online, изолируется от других отделов организации в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="96eb1-104">**Summary:** Configure a SharePoint Online team site that is isolated from the rest of the organization in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="96eb1-p101">SharePoint Online сайтов группы в Office 365, расположения для совместной работы, с помощью библиотеки общих документов, записной книжки OneNote и другие службы. Во многих случаях требуется широкий доступ и совместная работа между организаций или отделов. Тем не менее в некоторых случаях вы хотите жестко контролировать доступ и разрешения для сотрудничества между небольшой группы пользователей.</span><span class="sxs-lookup"><span data-stu-id="96eb1-p101">SharePoint Online team sites in Office 365 are locations for collaboration using a common document library, a OneNote notebook, and other services. In many cases, you want wide access and collaboration across departments or organizations. However, in some cases, you want to tightly control the access and permissions for collaboration among a small group of people.</span></span>
  
<span data-ttu-id="96eb1-p102">Доступ к SharePoint Online сайты рабочих групп и что могут делать пользователи управляет групп и уровней разрешений SharePoint. По умолчанию сайты SharePoint Online имеют три уровня доступа:</span><span class="sxs-lookup"><span data-stu-id="96eb1-p102">Access to SharePoint Online team sites and what users can do is controlled by SharePoint groups and permission levels. By default, SharePoint Online sites have three levels of access:</span></span>
  
- <span data-ttu-id="96eb1-110">**Члены**, пользователей, которые могут просматривать, создавать и изменять ресурсы на сайте.</span><span class="sxs-lookup"><span data-stu-id="96eb1-110">**Members**, who can view, create, and modify resources on the site.</span></span>
    
- <span data-ttu-id="96eb1-111">**Владельцы**, пользователей, которые имеют полный доступ к сайту, включая возможность изменения разрешений.</span><span class="sxs-lookup"><span data-stu-id="96eb1-111">**Owners**, who have complete control of the site, including the ability to change permissions.</span></span>
    
- <span data-ttu-id="96eb1-112">**Посетители**, кто может просматривать только ресурсы на сайте.</span><span class="sxs-lookup"><span data-stu-id="96eb1-112">**Visitors**, who only can view resources on the site.</span></span>
    
<span data-ttu-id="96eb1-p103">В этом статье действия по конфигурации изолированного SharePoint Online сайт группы для проекта секретный справочные материалы с именем ProjectX. Требования к access являются:</span><span class="sxs-lookup"><span data-stu-id="96eb1-p103">This article steps you through the configuration of an isolated SharePoint Online team site for a secret research project named ProjectX. The access requirements are:</span></span>
  
- <span data-ttu-id="96eb1-115">Только участники проекта могут получить доступ к сайту и его содержимому (документам, записной книжке OneNote, страницам), уровни разрешений SharePoint на просмотр и редактирование определяются членством в группе.</span><span class="sxs-lookup"><span data-stu-id="96eb1-115">Only members of the project can access the site and its contents (documents, OneNote Notebook, Pages), with edit and view SharePoint permission levels controlled through group membership.</span></span>
    
- <span data-ttu-id="96eb1-116">Только создатель сайта и члены группы администраторов сайта могут выполнять администрирование сайта, в том числе изменять разрешения на уровне сайта.</span><span class="sxs-lookup"><span data-stu-id="96eb1-116">Only the site creator and members of an Admins group for the site can perform site administration, which includes modifying site-level permissions.</span></span>
    
<span data-ttu-id="96eb1-117">Настройка изолированного сайта группы SharePoint Online в среде Office 365 для разработки и тестирования выполняется в три этапа:</span><span class="sxs-lookup"><span data-stu-id="96eb1-117">There are three phases to setting up an isolated SharePoint Online team site in your Office 365 dev/test environment:</span></span>
  
1. <span data-ttu-id="96eb1-118">Создание среды разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="96eb1-118">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="96eb1-119">Создание пользователей и групп для ProjectX.</span><span class="sxs-lookup"><span data-stu-id="96eb1-119">Create the users and groups for ProjectX.</span></span>
    
3. <span data-ttu-id="96eb1-120">Создание сайта группы SharePoint Online для ProjectX и его изоляция.</span><span class="sxs-lookup"><span data-stu-id="96eb1-120">Create a new ProjectX SharePoint Online team site and isolate it.</span></span>
    
> [!TIP]
> <span data-ttu-id="96eb1-121">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="96eb1-121">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="96eb1-122">Этап 1. Создание среды разработки и тестирования Office 365 — упрощенной или для имитированных предприятий</span><span class="sxs-lookup"><span data-stu-id="96eb1-122">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="96eb1-123">Если необходимо создать узел изолированного группы разработчиков SharePoint Online в облегченный путь с минимальным требованиям, следуйте инструкциям в этапы 2 и 3 [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="96eb1-123">If you just want to create an isolated SharePoint Online team site in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="96eb1-124">Если вы хотите создать узел изолированного группы разработчиков SharePoint Online в конфигурации имитации enterprise, следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="96eb1-124">If you want to create an isolated SharePoint Online team site in a simulated enterprise configuration, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="96eb1-p104">Для создания изолированного сайта SharePoint Online не требуется имитированная среда разработки и тестирования предприятия, которая включает имитированную интрасеть, подключенную к Интернету, и синхронизацию каталогов для леса Windows Server AD. Она указана здесь, чтобы вы могли протестировать изолированный сайт SharePoint Online и поэкспериментировать с ним в среде, которая представляет типичную среду для организаций.</span><span class="sxs-lookup"><span data-stu-id="96eb1-p104">Creating an isolated SharePoint Online site does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test an isolated SharePoint Online site and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a><span data-ttu-id="96eb1-127">Этап 2: Создание учетных записей пользователей и доступ к группам</span><span class="sxs-lookup"><span data-stu-id="96eb1-127">Phase 2: Create user accounts and access groups</span></span>

<span data-ttu-id="96eb1-128">Используйте инструкции из статьи [подключение к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) подключиться к своей подписке журнала Office 365, используя свою учетную запись глобального администратора из:</span><span class="sxs-lookup"><span data-stu-id="96eb1-128">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to connect to your Office 365 trail subscription with your global administrator account from:</span></span>
  
- <span data-ttu-id="96eb1-129">компьютера (для упрощенной среды разработки и тестирования Office 365);</span><span class="sxs-lookup"><span data-stu-id="96eb1-129">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="96eb1-130">виртуальной машины CLIENT1 (для среды Office 365 для разработки и тестирования смоделированного предприятия).</span><span class="sxs-lookup"><span data-stu-id="96eb1-130">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="96eb1-131">Чтобы создать новые группы доступа для ProjectX SharePoint Online сайт группы, выполните эти команды в командной строке Windows Azure модуль Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96eb1-131">To create the new access groups for the ProjectX SharePoint Online team site, run these commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> <span data-ttu-id="96eb1-132">Щелкните [здесь](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) для текстового файла, который содержит все команды PowerShell в данной статье.</span><span class="sxs-lookup"><span data-stu-id="96eb1-132">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) for a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="96eb1-133">Введите название организации (например, contosotoycompany) и двузначный код страны, а затем выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="96eb1-133">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="96eb1-134">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи привести конструктора и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="96eb1-134">From the display of the **New-MsolUser** command, note the generated password for the Lead Designer account and record it in a safe location.</span></span>
  
<span data-ttu-id="96eb1-135">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="96eb1-135">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="96eb1-136">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи привести исследователя и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="96eb1-136">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="96eb1-137">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="96eb1-137">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="96eb1-138">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи вице-президент по разработке и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="96eb1-138">From the display of the **New-MsolUser** command, note the generated password for the Development VP account and record it in a safe location.</span></span>
  
<span data-ttu-id="96eb1-139">Затем для добавления новых учетных записей для новых групп доступа, выполните следующие команды PowerShell в командной строке Windows Azure модуль Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="96eb1-139">Next, to add the new accounts to the new access groups, run these PowerShell commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

<span data-ttu-id="96eb1-140">Результаты:</span><span class="sxs-lookup"><span data-stu-id="96eb1-140">Results:</span></span>
  
- <span data-ttu-id="96eb1-141">Группа доступа членов ProjectX содержит привести Designer и привести исследователя учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="96eb1-141">The ProjectX-Members access group contains the Lead Designer and Lead Researcher user accounts</span></span>
    
- <span data-ttu-id="96eb1-142">Группа администраторов ProjectX доступа содержит учетной записи глобального администратора для пробной подписки</span><span class="sxs-lookup"><span data-stu-id="96eb1-142">The ProjectX-Admins access group contains the global administrator account for your trial subscription</span></span>
    
- <span data-ttu-id="96eb1-143">Группа доступа средства просмотра ProjectX содержит учетная запись вице-президент по разработке</span><span class="sxs-lookup"><span data-stu-id="96eb1-143">The ProjectX-Viewers access group contains the Development VP user account</span></span>
    
<span data-ttu-id="96eb1-144">На рисунке 1 показано доступа групп и их участия.</span><span class="sxs-lookup"><span data-stu-id="96eb1-144">Figure 1 shows the access groups and their membership.</span></span>
  
<span data-ttu-id="96eb1-145">**На рисунке 1**</span><span class="sxs-lookup"><span data-stu-id="96eb1-145">**Figure 1**</span></span>

![Группы Office 365 и их участники для изолированного сайта группы SharePoint Online](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a><span data-ttu-id="96eb1-147">Этап 3. Создание сайта группы SharePoint Online для ProjectX и его изоляция</span><span class="sxs-lookup"><span data-stu-id="96eb1-147">Phase 3: Create a new ProjectX SharePoint Online team site and isolate it</span></span>

<span data-ttu-id="96eb1-148">Чтобы создать сайт группы SharePoint Online для ProjectX, выполните перечисленные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="96eb1-148">To create a SharePoint Online team site for ProjectX, do the following:</span></span>
  
1. <span data-ttu-id="96eb1-149">С помощью браузера на одного локального компьютера (lightweight конфигурация) или на компьютере CLIENT1 (конфигурация имитации корпоративной) вход на портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя свою учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="96eb1-149">Using a browser on either your local computer (lightweight configuration) or on CLIENT1 (simulated enterprise configuration), sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="96eb1-150">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-150">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="96eb1-151">На новой вкладке SharePoint в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-151">On the new SharePoint tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="96eb1-p105">В поле **имя сайта группы**введите **ProjectX**. В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-p105">In **Team site name**, type **ProjectX**. In **Privacy settings**, select **Private - only members can access this site**.</span></span>
    
5. <span data-ttu-id="96eb1-154">В поле **Описание сайта группы**укажите **сайт SharePoint для ProjectX**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-154">In **Team site description**, type **SharePoint site for ProjectX**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="96eb1-155">На, **который вы хотите добавить**? области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-155">On the **Who do you want to add**? pane, click **Finish**.</span></span>
    
7. <span data-ttu-id="96eb1-156">На вкладке **Домашняя страница ProjectX** в браузере, в панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-156">On the new **ProjectX-Home** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
8. <span data-ttu-id="96eb1-157">В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-157">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
9. <span data-ttu-id="96eb1-158">В новом **разрешения: Project X** в браузере, щелкните **Параметры запроса доступа**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-158">In the new **Permissions: Project X** tab in your browser, click **Access Request Settings**.</span></span>
    
10. <span data-ttu-id="96eb1-159">В диалоговом окне **Параметры запросов доступа** снимите флажок **Разрешить участникам совместного использования сайтов и отдельных файлов и папок** и **Разрешить запросы доступа** (, чтобы все три флажка), а затем нажмите **кнопку ОК**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-159">In the **Access Requests Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
11. <span data-ttu-id="96eb1-160">Щелкните **ProjectX элементы** в списке.</span><span class="sxs-lookup"><span data-stu-id="96eb1-160">Click **ProjectX Members** in the list.</span></span>
    
12. <span data-ttu-id="96eb1-161">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-161">On the **People and Groups** page, click **New**.</span></span>
    
13. <span data-ttu-id="96eb1-162">В диалоговом окне **общий доступ** введите **ProjectX члены**, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-162">In the **Share** dialog box, type **ProjectX-Members**, select it, and then click **Share**.</span></span>
    
14. <span data-ttu-id="96eb1-163">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="96eb1-163">Click the back button on your browser.</span></span>
    
15. <span data-ttu-id="96eb1-164">В списке выберите **ProjectX владельцев** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-164">Click **ProjectX Owners** in the list.</span></span>
    
16. <span data-ttu-id="96eb1-165">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-165">On the **People and Groups** page, click **New**.</span></span>
    
17. <span data-ttu-id="96eb1-166">В диалоговом окне **общий доступ** введите **ProjectX Администраторы**, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-166">In the **Share** dialog box, type **ProjectX-Admins**, select it, and then click **Share**.</span></span>
    
18. <span data-ttu-id="96eb1-167">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="96eb1-167">Click the back button on your browser.</span></span>
    
19. <span data-ttu-id="96eb1-168">В списке выберите **Посетители ProjectX** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-168">Click **ProjectX Visitors** in the list.</span></span>
    
20. <span data-ttu-id="96eb1-169">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-169">On the **People and Groups** page, click **New**.</span></span>
    
21. <span data-ttu-id="96eb1-170">В диалоговом окне **общий доступ** **ProjectX-средства просмотра**типов, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-170">In the **Share** dialog box, type **ProjectX-Viewers**, select it, and then click **Share**.</span></span>
    
22. <span data-ttu-id="96eb1-171">Закройте вкладку **людей и групп** в браузере, перейдите на вкладку **Домашней ProjectX** в браузере, а затем закройте в области **разрешения для сайта** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-171">Close the **People and Groups** tab in your browser, click the **ProjectX-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="96eb1-172">Ниже представлены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="96eb1-172">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="96eb1-173">Группой SharePoint членов ProjectX содержит только группы доступа членов ProjectX (который содержит только привести Designer и привести исследователя учетные записи пользователей) и ProjectX (который содержит только учетная запись пользователя глобального администратора).</span><span class="sxs-lookup"><span data-stu-id="96eb1-173">The ProjectX Members SharePoint group contains only the ProjectX-Members access group (which contains only the Lead Designer and Lead Researcher user accounts) and the ProjectX group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="96eb1-174">Группы владельцев SharePoint ProjectX содержит только ProjectX-доступа к группе "Администраторы" (который содержит только учетная запись пользователя глобального администратора).</span><span class="sxs-lookup"><span data-stu-id="96eb1-174">The ProjectX Owners SharePoint group contains only the ProjectX-Admins access group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="96eb1-175">Используется группой SharePoint посетителей ProjectX содержит только группу доступа средства просмотра ProjectX (который содержит только учетная запись пользователя вице-президент по разработке).</span><span class="sxs-lookup"><span data-stu-id="96eb1-175">The ProjectX Visitors SharePoint group contains only the ProjectX-Viewers access group (which contains only the Development VP user account).</span></span>
    
- <span data-ttu-id="96eb1-176">Участники не могут изменять разрешения на уровне сайта (это могут делать только члены группы ProjectX-Admins).</span><span class="sxs-lookup"><span data-stu-id="96eb1-176">Members cannot modify site-level permissions (this can only be done by members of the ProjectX-Admins group).</span></span>
    
- <span data-ttu-id="96eb1-177">Другие учетные записи пользователей не могут получить доступ к сайту и его ресурсам и запросить доступ к нему.</span><span class="sxs-lookup"><span data-stu-id="96eb1-177">Other user accounts cannot access the site or its resources or request access to the site.</span></span>
    
<span data-ttu-id="96eb1-178">На рисунке 2 показаны группы SharePoint и их участники.</span><span class="sxs-lookup"><span data-stu-id="96eb1-178">Figure 2 shows the SharePoint groups and their membership.</span></span>
  
<span data-ttu-id="96eb1-179">**На рисунке 2**</span><span class="sxs-lookup"><span data-stu-id="96eb1-179">**Figure 2**</span></span>

![Группы SharePoint Online и их участники для изолированного сайта группы SharePoint Online](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
<span data-ttu-id="96eb1-181">Теперь давайте демонстрации access с помощью учетной записи пользователя привести конструктора:</span><span class="sxs-lookup"><span data-stu-id="96eb1-181">Now let's demonstrate access using the Lead Designer user account:</span></span>
  
1. <span data-ttu-id="96eb1-182">Закройте вкладке **Главная ProjectX** в браузере и затем перейдите на вкладку **Microsoft Office для дома** в браузере.</span><span class="sxs-lookup"><span data-stu-id="96eb1-182">Close the **ProjectX-Home** tab in your browser, and then click the **Microsoft Office Home** tab in your browser.</span></span>
    
2. <span data-ttu-id="96eb1-183">Щелкните имя глобального администратора и нажмите кнопку **Выход**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-183">Click the name of your global administrator, and then click **Sign out**.</span></span>
    
3. <span data-ttu-id="96eb1-184">Войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)), с помощью конструктора привести имя учетной записи и пароль.</span><span class="sxs-lookup"><span data-stu-id="96eb1-184">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Lead Designer account name and its password.</span></span>
    
4. <span data-ttu-id="96eb1-185">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-185">In the list of tiles, click **SharePoint**.</span></span>
    
5. <span data-ttu-id="96eb1-p106">На новой вкладке **SharePoint** в браузере в поле «Поиск» введите **ProjectX** активировать поиска и выберите пункт сайт группы **ProjectX** . Вы должны увидеть новую вкладку в браузере для сайта группы ProjectX.</span><span class="sxs-lookup"><span data-stu-id="96eb1-p106">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
6. <span data-ttu-id="96eb1-p107">Щелкните значок параметры. Обратите внимание, что параметр не для **Разрешения для сайта**. Это правильно, так как только члены группы «Администраторы» ProjectX можно изменить разрешения на сайте</span><span class="sxs-lookup"><span data-stu-id="96eb1-p107">Click the settings icon. Notice that there is no option for **Site Permissions**. This is correct because only the members of the ProjectX-Admins group can modify permissions on the site</span></span>
    
7. <span data-ttu-id="96eb1-191">Откройте приложение "Блокнот" или другой текстовый редактор.</span><span class="sxs-lookup"><span data-stu-id="96eb1-191">Open Notepad or a text editor of your choice.</span></span>
    
8. <span data-ttu-id="96eb1-192">Скопируйте URL-адрес сайта группы ProjectX и вставьте его в новой строке в приложении "Блокнот" или другом текстовом редакторе.</span><span class="sxs-lookup"><span data-stu-id="96eb1-192">Copy the URL of the ProjectX team site and paste it on a new line in Notepad or your text editor.</span></span>
    
9. <span data-ttu-id="96eb1-193">На вкладке **Главная ProjectX** новый в браузере выберите **документы**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-193">On the new **ProjectX-Home** tab in your browser, click **Documents**.</span></span>
    
10. <span data-ttu-id="96eb1-194">Скопируйте URL-адрес папки документов ProjectX и вставьте его в новой строке в Блокноте или другом текстовом редакторе.</span><span class="sxs-lookup"><span data-stu-id="96eb1-194">Copy the URL of the ProjectX documents folder and paste it on a new line in Notepad or your text editor.</span></span>
    
11. <span data-ttu-id="96eb1-195">На новой вкладке **ProjectX документы** в браузере, щелкните **Создать > документ Word**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-195">On the new **ProjectX-Documents** tab in your browser, click **New > Word document**.</span></span>
    
12. <span data-ttu-id="96eb1-p108">Введите текст в **Word Online** страницы, дождитесь состояния для указания **сохранения**, нажмите кнопку Назад в браузере и затем обновить страницу. Вы должны увидеть новые **Document.docx** в папку « **документы** ».</span><span class="sxs-lookup"><span data-stu-id="96eb1-p108">Type some text in the **Word Online** page, wait for the status to indicate **Saved**, click the back button on your browser, and then refresh the page. You should see a new **Document.docx** in the **Documents** folder.</span></span>
    
13. <span data-ttu-id="96eb1-198">Нажмите кнопку с многоточием для документа **Document.docx** и нажмите кнопку **получить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-198">Click the ellipsis for the **Document.docx** document, and then click **Get a link**.</span></span>
    
14. <span data-ttu-id="96eb1-199">Скопируйте URL-адрес в диалоговом окне **общий доступ «Document.docx»** и вставьте его на новую строку в блокноте или текстовый редактор, а затем закройте диалоговое окно **«Document.docx» общий доступ** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-199">Copy the URL in the **Share 'Document.docx'** dialog box and paste it on a new line in Notepad or your text editor, and then close the **Share 'Document.docx'** dialog box.</span></span>
    
15. <span data-ttu-id="96eb1-200">Закройте вкладки **ProjectX документы** и **SharePoint** в браузере и затем перейдите на вкладку **Microsoft Office для дома** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-200">Close the **ProjectX-Documents** and **SharePoint** tabs in your browser, and then click the **Microsoft Office Home** tab.</span></span>
    
16. <span data-ttu-id="96eb1-201">Щелкните имя **Привести конструктора** и нажмите кнопку **Выход**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-201">Click the **Lead Designer** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="96eb1-202">Теперь давайте демонстрации access с помощью учетной записи пользователя вице-президент по разработке:</span><span class="sxs-lookup"><span data-stu-id="96eb1-202">Now let's demonstrate access using the Development VP user account:</span></span>
  
1. <span data-ttu-id="96eb1-203">Войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)), вице-президент по разработке имя учетной записи и пароль, его.</span><span class="sxs-lookup"><span data-stu-id="96eb1-203">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Development VP account name and its password.</span></span>
    
2. <span data-ttu-id="96eb1-204">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-204">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="96eb1-p109">На новой вкладке **SharePoint** в браузере в поле «Поиск» введите **ProjectX** активировать поиска и выберите пункт сайт группы **ProjectX** . Вы должны увидеть новую вкладку в браузере для сайта группы ProjectX.</span><span class="sxs-lookup"><span data-stu-id="96eb1-p109">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
4. <span data-ttu-id="96eb1-207">Щелкните **документы**и выберите файл **Document.docx** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-207">Click **Documents**, and then click the **Document.docx** file.</span></span>
    
5. <span data-ttu-id="96eb1-p110">На вкладке **Document.docx** в браузере попробуйте изменить текст. Должно появиться сообщение о том, **Этот документ доступен только для чтения.** Ожидается, что это так, как учетная запись пользователя вице-президент по разработке имеет только просмотр разрешений для сайта.</span><span class="sxs-lookup"><span data-stu-id="96eb1-p110">In the **Document.docx** tab in your browser, try to modify the text. You should see a message stating **This document is read-only.** This is expected because the Development VP user account only has view permissions for the site.</span></span>
    
6. <span data-ttu-id="96eb1-211">Закройте вкладки **Document.docx**, **ProjectX документы**и **SharePoint** в браузере.</span><span class="sxs-lookup"><span data-stu-id="96eb1-211">Close the **Document.docx**, **ProjectX-Documents**, and **SharePoint** tabs in your browser.</span></span>
    
7. <span data-ttu-id="96eb1-212">Перейдите на вкладку **Microsoft Office для дома** , щелкните имя **Вице-президент по разработке** и нажмите кнопку **Выход**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-212">Click the **Microsoft Office Home** tab, click the **Development VP** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="96eb1-213">Теперь давайте Демонстрация доступ с помощью учетной записи пользователя, которая не имеет разрешений:</span><span class="sxs-lookup"><span data-stu-id="96eb1-213">Now let's demonstrate access with a user account that has no permissions:</span></span>
  
1. <span data-ttu-id="96eb1-214">Войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)), с помощью 3 пользователя имя учетной записи и пароль.</span><span class="sxs-lookup"><span data-stu-id="96eb1-214">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the User 3 account name and its password.</span></span>
    
2. <span data-ttu-id="96eb1-215">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-215">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="96eb1-p111">На новой вкладке **SharePoint** в браузере в поле «Поиск» введите **ProjectX** и затем активируйте поиска. Должно появиться сообщение **не соответствует операции поиска.**</span><span class="sxs-lookup"><span data-stu-id="96eb1-p111">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box and then activate the search. You should see the message **Nothing here matches your search.**</span></span>
    
4. <span data-ttu-id="96eb1-p112">Скопируйте URL-адрес для сайта ProjectX в адресной строке браузера open экземпляр блокнота или текстового редактора и нажмите клавишу **Ввод**. Вы должны увидеть страницу **Отказано в доступе** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-p112">From the open instance of Notepad or your text editor, copy the URL for the ProjectX site into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
5. <span data-ttu-id="96eb1-p113">В "Блокнот" или текстовый редактор скопируйте URL-адрес для папки ProjectX документы в адресной строке браузера и нажмите клавишу **Ввод**. Вы должны увидеть страницу **Отказано в доступе** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-p113">From Notepad or your text editor, copy the URL for the ProjectX Documents folder into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
6. <span data-ttu-id="96eb1-p114">В "Блокнот" или текстовый редактор скопируйте URL-адрес для файла Documents.docx в адресной строке браузера и нажмите клавишу **Ввод**. Вы должны увидеть страницу **Отказано в доступе** .</span><span class="sxs-lookup"><span data-stu-id="96eb1-p114">From Notepad or your text editor, copy the URL for the Documents.docx file into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
7. <span data-ttu-id="96eb1-224">Закройте вкладку **SharePoint** в браузере, перейдите на вкладку **Microsoft Office для дома** , щелкните имя **пользователя 3** и нажмите кнопку **Выход**.</span><span class="sxs-lookup"><span data-stu-id="96eb1-224">Close the **SharePoint** tab in your browser, click the **Microsoft Office Home** tab, click the **User 3** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="96eb1-225">Изолированный сайта SharePoint Online готов к дополнительные экспериментов.</span><span class="sxs-lookup"><span data-stu-id="96eb1-225">Your isolated SharePoint Online site is now ready for your additional experimentation.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="96eb1-226">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="96eb1-226">Next Step</span></span>

<span data-ttu-id="96eb1-227">Когда вы будете готовы выполнить развертывание изолированного сайта группы SharePoint Online в рабочей среде, просмотрите подробные инструкции из статьи [Разработка изолированного сайта группы SharePoint Online](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="96eb1-227">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="96eb1-228">См. также</span><span class="sxs-lookup"><span data-stu-id="96eb1-228">See Also</span></span>

[<span data-ttu-id="96eb1-229">Изолированные сайты групп SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="96eb1-229">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="96eb1-230">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="96eb1-230">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="96eb1-231">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="96eb1-231">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="96eb1-232">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="96eb1-232">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="96eb1-233">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="96eb1-233">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




