---
title: "Развертывание изолированного сайта группы SharePoint Online"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: "Сводка: Развертывание нового изолированного SharePoint Online сайта группы с помощью этих пошаговые инструкции."
ms.openlocfilehash: 9715c6168276b6ba9ffc63591cc6421708bbda27
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="45192-103">Развертывание изолированного сайта группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45192-103">Deploy an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="45192-104">**Сводка:** Развертывание нового изолированного SharePoint Online сайта группы с помощью этих пошаговые инструкции.</span><span class="sxs-lookup"><span data-stu-id="45192-104">**Summary:** Deploy a new isolated SharePoint Online team site with these step-by-step instructions.</span></span>
  
<span data-ttu-id="45192-p101">Эта статья представляет собой пошаговое руководство по созданию и настройке изолированного сайта группы SharePoint Online в Microsoft Office 365. Эти инструкции предполагают использование трех групп SharePoint по умолчанию и соответствующих уровней разрешений (по одной группе доступа на основе Azure Active Directory (AD) для каждого уровня доступа).</span><span class="sxs-lookup"><span data-stu-id="45192-p101">This article is a step-by-step deployment guide for creating and configuring an isolated SharePoint Online team site in Microsoft Office 365. These steps assume the use of the three default SharePoint groups and corresponding permission levels, with a single Azure Active Directory (AD)-based access group for each level of access.</span></span>
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a><span data-ttu-id="45192-107">Этап 1: Создание и заполнение группы доступа группы сайтов</span><span class="sxs-lookup"><span data-stu-id="45192-107">Phase 1: Create and populate the team site access groups</span></span>

<span data-ttu-id="45192-108">На этом этапе вы создаете три группы доступа на основе Azure AD для трех групп SharePoint по умолчанию и заполняете их соответствующими учетными записями пользователей.</span><span class="sxs-lookup"><span data-stu-id="45192-108">In this phase, you create the three Azure AD-based access groups for the three default SharePoint groups and populate them with the appropriate user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="45192-p102">При выполнении последующих шагов предполагается, что все необходимые учетные записи пользователей уже существуют и для них назначены соответствующие лицензии. Если это не сделано, завершите требуемые действия, прежде чем переходить к шагу 1.</span><span class="sxs-lookup"><span data-stu-id="45192-p102">The following steps assume that all necessary user accounts already exist and are assigned the appropriate licenses. If not, please add them and assign licenses before proceeding to step 1.</span></span> 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a><span data-ttu-id="45192-111">Шаг 1. Составление списка администраторов сайта SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45192-111">Step 1: List the SharePoint Online admins for the site</span></span>

<span data-ttu-id="45192-112">Определите набор учетных записей пользователей для администраторов изолированного сайта группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="45192-112">Determine the set of user accounts corresponding to the SharePoint Online admins for the isolated team site.</span></span>
  
<span data-ttu-id="45192-113">Если вы управляете учетными записями и группами пользователей с помощью Office 365 и хотите использовать Windows PowerShell, составьте список имен участников-пользователей (например, marthaa@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="45192-113">If you are managing user accounts and groups through Office 365 and want to use Windows PowerShell, make a list of their user principal names (UPNs) (example UPN: belindan@contoso.com).</span></span>
  
### <a name="step-2-list-the-members-for-the-site"></a><span data-ttu-id="45192-114">Шаг 2. Составление списка участников сайта</span><span class="sxs-lookup"><span data-stu-id="45192-114">Step 2: List the members for the site</span></span>

<span data-ttu-id="45192-115">Определите набор учетных записей пользователей для участников изолированного сайта группы, т. е. для тех, кто будет совместно работать с ресурсами, хранящимися на сайте.</span><span class="sxs-lookup"><span data-stu-id="45192-115">Determine the set of user accounts corresponding to the members for the isolated team site, those who will be collaborating on resources stored within the site.</span></span>
  
<span data-ttu-id="45192-p103">Если вы управляете учетными записями и группами пользователей с помощью Office 365 и планируете использовать PowerShell, составьте список имен участников-пользователей. Если на сайте много участников, вы можете сохранить список имен участников-пользователей в текстовом файле и добавить их все с помощью одной команды PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45192-p103">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
### <a name="step-3-list-the-viewers-for-the-site"></a><span data-ttu-id="45192-118">Шаг 3. Составление списка посетителей сайта</span><span class="sxs-lookup"><span data-stu-id="45192-118">Step 3: List the viewers for the site</span></span>

<span data-ttu-id="45192-119">Определите набор учетных записей пользователей для посетителей изолированного сайта группы, т. е. для тех, кто может просматривать ресурсы, хранящиеся на сайте, но не может изменять их или напрямую совместно работать с их содержимым.</span><span class="sxs-lookup"><span data-stu-id="45192-119">Determine the set of user accounts corresponding to the viewers of the isolated team site, those who can view the resources stored in the site but not modify them or directly collaborate on their contents.</span></span>
  
<span data-ttu-id="45192-p104">Если вы управляете учетными записями и группами пользователей с помощью Office 365 и планируете использовать PowerShell, составьте список имен участников-пользователей. Если на сайте много участников, вы можете сохранить список имен участников-пользователей в текстовом файле и добавить их все с помощью одной команды PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45192-p104">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
<span data-ttu-id="45192-122">Читателями сайта могут быть руководители, юрисконсульты или межведомственные заинтересованные лица.</span><span class="sxs-lookup"><span data-stu-id="45192-122">Viewers for the site might include executive management, legal counsel, or inter-departmental stakeholders.</span></span>
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a><span data-ttu-id="45192-123">Шаг 4. Создание трех групп доступа для сайта в Azure AD</span><span class="sxs-lookup"><span data-stu-id="45192-123">Step 4: Create the three access groups for the site in Azure AD</span></span>

<span data-ttu-id="45192-124">Вам нужно создать в Azure AD следующие группы доступа:</span><span class="sxs-lookup"><span data-stu-id="45192-124">You need to create the following access groups in Azure AD:</span></span>
  
- <span data-ttu-id="45192-125">Администраторы сайта (список из шага 1)</span><span class="sxs-lookup"><span data-stu-id="45192-125">Site admins (which will contain the list from step 1)</span></span>
    
- <span data-ttu-id="45192-126">Участники сайта (список из шага 2)</span><span class="sxs-lookup"><span data-stu-id="45192-126">Site members (which will contain the list from step 2)</span></span>
    
- <span data-ttu-id="45192-127">Читатели сайта (список из шага 3)</span><span class="sxs-lookup"><span data-stu-id="45192-127">Site viewers (which will contain the list from step 3)</span></span>
    
1. <span data-ttu-id="45192-128">В браузере перейдите на портале Azure по [https://portal.azure.com](https://portal.azure.com) и вход с помощью учетных данных учетной записи, которая была назначена с ролью Администратор управления пользователями или администратор компании.</span><span class="sxs-lookup"><span data-stu-id="45192-128">In your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com) and sign in with the credentials of an account that has been assigned with User Management Admin or Company Administrator role.</span></span>
    
2. <span data-ttu-id="45192-129">На портале Azure щелкните **Azure Active Directory > пользователи и группы > все группы**.</span><span class="sxs-lookup"><span data-stu-id="45192-129">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="45192-130">На blade **все группы** нажмите кнопку **+ новую группу**.</span><span class="sxs-lookup"><span data-stu-id="45192-130">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="45192-131">На blade **группы** :</span><span class="sxs-lookup"><span data-stu-id="45192-131">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="45192-132">В поле **имя**введите имя группы.</span><span class="sxs-lookup"><span data-stu-id="45192-132">Type the group name in **Name**.</span></span>
    
  - <span data-ttu-id="45192-133">Выберите **назначенные** **членства**.</span><span class="sxs-lookup"><span data-stu-id="45192-133">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="45192-134">Для **включения Office компонентов**, нажмите кнопку **Да** .</span><span class="sxs-lookup"><span data-stu-id="45192-134">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="45192-135">Нажмите кнопку **Создать**, а затем закройте blade **группы** .</span><span class="sxs-lookup"><span data-stu-id="45192-135">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="45192-136">Повторите шаги 3 – 5 для дополнительных групп.</span><span class="sxs-lookup"><span data-stu-id="45192-136">Repeat steps 3-5 for your additional groups.</span></span>
    
> [!NOTE]
> <span data-ttu-id="45192-p105">Необходимо использовать Azure портала для создания групп, чтобы они имеют включенными компонентами Office. Если сайт SharePoint Online изолированной более поздней версии настроен как конфиденциальными сайта с подписью защиты информации Azure (AIP) для шифрования файлов и назначения разрешений для определенных групп, разрешенных групп необходимо создать с помощью средства Office включено. Параметр функции Office группы Azure AD не может изменить после его создания.</span><span class="sxs-lookup"><span data-stu-id="45192-p105">You need to use the Azure portal to create the groups so that they have Office features enabled. If a SharePoint Online isolated site is later configured as a Highly Confidential site with an Azure Information Protection (AIP) label to encrypt files and assign permission to specific groups, the permitted groups must have been created with Office features enabled. You cannot change the Office features setting of an Azure AD group after it has been created.</span></span> 
  
<span data-ttu-id="45192-140">Ниже приведен результирующий конфигурации с группами доступа три сайта.</span><span class="sxs-lookup"><span data-stu-id="45192-140">Here is your resulting configuration with the three site access groups.</span></span>
  
![Три группы доступа для развертывания изолированного сайта SharePoint Online.](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a><span data-ttu-id="45192-p106">Шаг 5. Добавление учетных записей пользователей в группы доступа</span><span class="sxs-lookup"><span data-stu-id="45192-p106">Step 5. Add the user accounts to the access groups</span></span>

<span data-ttu-id="45192-144">На этом шаге выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="45192-144">In this step, do the following:</span></span>
  
1. <span data-ttu-id="45192-145">Добавьте список пользователей из шага 1 в группу доступа для администраторов сайта.</span><span class="sxs-lookup"><span data-stu-id="45192-145">Add the list of users from step 1 to the site admins access group</span></span>
    
2. <span data-ttu-id="45192-146">Добавьте список пользователей из шага 2 в группу доступа для участников сайта.</span><span class="sxs-lookup"><span data-stu-id="45192-146">Add the list of users from step 2 to the site members access group</span></span>
    
3. <span data-ttu-id="45192-147">Добавьте список пользователей из шага 3 в группу доступа для читателей сайта.</span><span class="sxs-lookup"><span data-stu-id="45192-147">Add the list of users from step 3 to the site viewers access group</span></span>
    
<span data-ttu-id="45192-148">Если вы управляете учетными записями и группами пользователей с помощью Windows Server AD, добавьте пользователей в соответствующие группы доступа, выполнив стандартные процедуры управления пользователями и группами в Windows Server AD, и дождитесь синхронизации со своей подпиской на Office 365.</span><span class="sxs-lookup"><span data-stu-id="45192-148">If you are managing user accounts and groups through Windows Server AD, add users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="45192-p107">Если вы управляете учетными записями и группами пользователей с помощью Office 365, вы можете воспользоваться Центром администрирования Office или PowerShell. Если имена групп доступа повторяются, следует воспользоваться Центром администрирования Office.</span><span class="sxs-lookup"><span data-stu-id="45192-p107">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell. If you have duplicate group names for any of the access groups, you should use the Office Admin center.</span></span>
  
<span data-ttu-id="45192-151">По центру администрирования Office вход с помощью учетной записи пользователя, которому назначена роль пользователя учетной записи администратора или администратора компании и используйте группы, чтобы добавить соответствующие учетные записи пользователей и групп в группы соответствующие права доступа.</span><span class="sxs-lookup"><span data-stu-id="45192-151">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate user accounts and groups to the appropriate access groups.</span></span>
  
<span data-ttu-id="45192-152">Если вы используете PowerShell, сначала [подключитесь с помощью модуля Azure Active Directory PowerShell 2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="45192-152">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="45192-153">Затем используйте следующий блок команды для добавления учетной записи отдельного пользователя в группу доступа:</span><span class="sxs-lookup"><span data-stu-id="45192-153">Next, use the following command block to add an individual user account to an access group:</span></span>
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="45192-154">Текстовый файл со всеми командами PowerShell и лист Excel для создания команд PowerShell на основе имен групп и учетных записей пользователей вы найдете в [комплекте средств для развертывания изолированного сайта группы SharePoint Online](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span><span class="sxs-lookup"><span data-stu-id="45192-154">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 
  
<span data-ttu-id="45192-155">Если вы сохранили имена участников-пользователей для учетных записей пользователей какой-либо из групп доступа в текстовом файле, воспользуйтесь следующим блоком команд PowerShell, чтобы добавить их все сразу:</span><span class="sxs-lookup"><span data-stu-id="45192-155">If you stored the UPNs of user accounts for any of the access groups in a text file, you can use the following PowerShell command block to add them all at one time:</span></span>
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

<span data-ttu-id="45192-156">Для PowerShell используйте следующий блок команды для добавления отдельных группы в группу доступа:</span><span class="sxs-lookup"><span data-stu-id="45192-156">For PowerShell, use the following command block to add an individual group to an access group:</span></span>
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

<span data-ttu-id="45192-157">Результаты должны выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="45192-157">The results should be the following:</span></span>
  
- <span data-ttu-id="45192-158">Группы сайтов Администраторы Azure AD содержит учетных записей администратора сайта или группы</span><span class="sxs-lookup"><span data-stu-id="45192-158">The site admins Azure AD group contains the site admin user accounts or groups</span></span>
    
- <span data-ttu-id="45192-159">Azure AD группы участников сайта содержит сайт учетные записи пользователей или групп</span><span class="sxs-lookup"><span data-stu-id="45192-159">The site members Azure AD group contains the site member user accounts or groups</span></span>
    
- <span data-ttu-id="45192-160">Группа просматривающих отчеты пользователей Azure AD сайт содержит учетные записи пользователей или групп, которые можно просматривать только содержимое сайта</span><span class="sxs-lookup"><span data-stu-id="45192-160">The site viewers Azure AD group contains the user accounts or groups that can only view the site contents</span></span>
    
<span data-ttu-id="45192-161">Проверьте список участников для каждой группы доступа в Центре администрирования Office или с помощью следующего блока команд PowerShell:</span><span class="sxs-lookup"><span data-stu-id="45192-161">Validate the list of group members for each access group with the Office Admin center or with the following PowerShell command block:</span></span>
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

<span data-ttu-id="45192-162">Ниже приведен результирующий конфигурации с группами доступа три сайта, заполненный учетных записей пользователей или групп.</span><span class="sxs-lookup"><span data-stu-id="45192-162">Here is your resulting configuration with the three site access groups populated with user accounts or groups.</span></span>
  
![Три группы доступа, заполненные данными учетных записей пользователей.](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a><span data-ttu-id="45192-164">Этап 2. Создание и настройка изолированного сайта группы</span><span class="sxs-lookup"><span data-stu-id="45192-164">Phase 2: Create and configure the isolated team site</span></span>

<span data-ttu-id="45192-165">На этом этапе вы создаете изолированный сайт SharePoint Online и настраиваете разрешения в соответствии с уровнями разрешений SharePoint Online по умолчанию, чтобы можно было использовать ваши новые группы доступа на основе Azure AD.</span><span class="sxs-lookup"><span data-stu-id="45192-165">In this phase, you create the isolated SharePoint Online site and configure the permissions for the default SharePoint Online permission levels to use your new Azure AD-based access groups.</span></span>
  
<span data-ttu-id="45192-166">Сначала создайте сайт группы SharePoint Online, следуя приведенным ниже инструкциям.</span><span class="sxs-lookup"><span data-stu-id="45192-166">First, create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="45192-p108">Войдите в портал Office 365 с использованием учетной записи, которая также будет использоваться для администрирования SharePoint Online сайта группы (администратору SharePoint Online). Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="45192-p108">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="45192-169">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="45192-169">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="45192-170">На вкладке **SharePoint** нового окна браузера нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="45192-170">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="45192-171">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="45192-171">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="45192-172">В поле **имя узла**введите имя сайта группы.</span><span class="sxs-lookup"><span data-stu-id="45192-172">In **Site name**, type a name for the team site.</span></span> 
    
6. <span data-ttu-id="45192-173">В **поле Описание сайта группы** введите необязательное описание назначения сайта.</span><span class="sxs-lookup"><span data-stu-id="45192-173">In **Team site description,** type an optional description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="45192-174">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="45192-174">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="45192-175">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="45192-175">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="45192-176">Далее настройте разрешения на новом сайте группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="45192-176">Next, from the new SharePoint Online team site, configure permissions.</span></span>
  
1. <span data-ttu-id="45192-177">В панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="45192-177">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
2. <span data-ttu-id="45192-178">В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="45192-178">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
3. <span data-ttu-id="45192-179">На вкладке **разрешения** нового браузера щелкните **Параметры запроса доступа**.</span><span class="sxs-lookup"><span data-stu-id="45192-179">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
4. <span data-ttu-id="45192-180">В диалоговом окне **Параметры запросов доступа** снимите флажок **Разрешить члена для совместного использования сайтов и отдельных файлов и папок** и **Разрешить запросы доступа** (, чтобы все три флажка), а затем нажмите **кнопку ОК**.</span><span class="sxs-lookup"><span data-stu-id="45192-180">In the **Access Requests Settings** dialog box, clear **Allow member to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
5. <span data-ttu-id="45192-181">На вкладке **разрешения** браузера щелкните ** \<имя сайта > члены** в списке.</span><span class="sxs-lookup"><span data-stu-id="45192-181">On the **Permissions** tab of your browser, click **\<site name> Members** in the list.</span></span>
    
6. <span data-ttu-id="45192-182">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="45192-182">In **People and Groups**, click **New**.</span></span>
    
7. <span data-ttu-id="45192-183">В диалоговом окне **общий доступ** введите имя группы доступа участников сайта, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="45192-183">In the **Share** dialog box, type the name of the site members access group, select it, and then click **Share**.</span></span>
    
8. <span data-ttu-id="45192-184">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="45192-184">Click the back button on your browser.</span></span>
    
9. <span data-ttu-id="45192-185">Нажмите кнопку ** \<имя сайта > владельцев** в списке.</span><span class="sxs-lookup"><span data-stu-id="45192-185">Click **\<site name> Owners** in the list.</span></span>
    
10. <span data-ttu-id="45192-186">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="45192-186">In **People and Groups**, click **New**.</span></span>
    
11. <span data-ttu-id="45192-187">В диалоговом окне **общий доступ** введите имя группы доступа Администраторы сайта, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="45192-187">In the **Share** dialog box, type the name of the site admins access group, select it, and then click **Share**.</span></span>
    
12. <span data-ttu-id="45192-188">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="45192-188">Click the back button on your browser.</span></span>
    
13. <span data-ttu-id="45192-189">Нажмите кнопку ** \<имя сайта > посетители** в списке.</span><span class="sxs-lookup"><span data-stu-id="45192-189">Click **\<site name> Visitors** in the list.</span></span>
    
14. <span data-ttu-id="45192-190">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="45192-190">In **People and Groups**, click **New**.</span></span>
    
15. <span data-ttu-id="45192-191">В диалоговом окне **общий доступ** введите имя группы доступа средства просмотра сайта, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="45192-191">In the **Share** dialog box, type the name of the site viewers access group, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="45192-192">Закройте вкладку **разрешения** браузера.</span><span class="sxs-lookup"><span data-stu-id="45192-192">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="45192-193">Ознакомьтесь с результатами настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="45192-193">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="45192-194">** \<Имя сайта > владельцев** группы SharePoint содержит сайт доступа к группе "Администраторы", в которых все участники иметь уровень разрешений **полного доступа** .</span><span class="sxs-lookup"><span data-stu-id="45192-194">The **\<site name> Owners** SharePoint group contains the site admins access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="45192-195">** \<Имя сайта > члены** группы SharePoint содержит группы участников сайта доступа, в которой все члены имеют **Изменить** разрешения.</span><span class="sxs-lookup"><span data-stu-id="45192-195">The **\<site name> Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="45192-196">** \<Имя сайта > посетители** группы SharePoint содержит группу доступа средства просмотра сайтов, в которых все участники иметь уровень разрешений **Чтение** .</span><span class="sxs-lookup"><span data-stu-id="45192-196">The **\<site name> Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="45192-197">Возможности для участников пригласить других участников или от членов запросить доступ отключен.</span><span class="sxs-lookup"><span data-stu-id="45192-197">The ability for members to invite other members or for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="45192-198">Ниже приведен результирующий конфигурации с тремя групп SharePoint для сайта настроены на использование три группы доступа, которые заполняются учетных записей пользователей или групп Azure AD.</span><span class="sxs-lookup"><span data-stu-id="45192-198">Here is your resulting configuration with the three SharePoint groups for the site configured to use the three access groups, which are populated with user accounts or Azure AD groups.</span></span>
  
![Окончательная конфигурация изолированного сайта SharePoint Online с группами доступа и учетными записями пользователей.](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
<span data-ttu-id="45192-200">Теперь вы и участники сайта можете совместно работать с его материалами посредством участия в одной из групп доступа.</span><span class="sxs-lookup"><span data-stu-id="45192-200">You and the members of the site, through group membership in one of the access groups, can now collaborate using the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="45192-201">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="45192-201">Next step</span></span>

<span data-ttu-id="45192-202">При необходимости изменить членство в группе доступ сайта или создайте папку документов с помощью пользовательских разрешений см [изолированной SharePoint Online сайт группы](manage-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="45192-202">When you need to change site access group membership or create a document folder with custom permissions, see [Manage an isolated SharePoint Online team site](manage-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="45192-203">See Also</span><span class="sxs-lookup"><span data-stu-id="45192-203">See Also</span></span>

[<span data-ttu-id="45192-204">Изолированные сайты групп SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45192-204">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="45192-205">Разработка изолированного сайта группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45192-205">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="45192-206">Управление изолированным сайтом группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="45192-206">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="45192-207">Решения для обеспечения безопасности</span><span class="sxs-lookup"><span data-stu-id="45192-207">Security solutions</span></span>](security-solutions.md)



