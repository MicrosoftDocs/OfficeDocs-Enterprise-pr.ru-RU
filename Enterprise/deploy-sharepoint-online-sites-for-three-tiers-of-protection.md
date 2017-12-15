---
title: "Развертывание сайтов SharePoint Online для три уровня защиты"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "Сводка: Создание и настройка SharePoint Online сайты рабочих групп для различных уровнях защита информации."
ms.openlocfilehash: 1023eff2542ab1bf41a8261d85d70c06718497cf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="d52eb-103">Развертывание сайтов SharePoint Online для три уровня защиты</span><span class="sxs-lookup"><span data-stu-id="d52eb-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="d52eb-104">**Сводка:** Создание и настройка SharePoint Online сайты рабочих групп для различных уровнях защита информации.</span><span class="sxs-lookup"><span data-stu-id="d52eb-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="d52eb-p101">Проектирование и развертывание базового, конфиденциальных и конфиденциальными сайтов SharePoint Online группы используйте действия, описанные в этой статье. Дополнительные сведения об этих трех уровней защиты можно [безопасного SharePoint Online сайтами и файлами](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="d52eb-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="d52eb-107">Базовые сайты группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d52eb-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="d52eb-p102">Базовая защита распространяется на общедоступный и частный сайты группы. Общедоступные сайты группы может найти и открыть любой пользователь в организации. Частный сайт группы могут найти и открыть только члены группы Office 365, связанной с этим сайтом. Оба типа сайтов группы позволяют участникам делиться содержимым сайта.</span><span class="sxs-lookup"><span data-stu-id="d52eb-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="d52eb-112">Общедоступный</span><span class="sxs-lookup"><span data-stu-id="d52eb-112">Public</span></span>

<span data-ttu-id="d52eb-113">Чтобы создать базовый сайт группы SharePoint Online с условиями доступа и разрешениями, предусмотренными для общедоступного сайта:</span><span class="sxs-lookup"><span data-stu-id="d52eb-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="d52eb-p103">Войдите в портал Office 365 с использованием учетной записи, которая также будет использоваться для администрирования SharePoint Online сайта группы (администратору SharePoint Online). Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d52eb-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d52eb-116">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d52eb-117">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d52eb-118">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d52eb-119">В поле **имя узла**введите имя сайта общей группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="d52eb-120">В поле **Описание сайта группы**введите описание назначения сайта.</span><span class="sxs-lookup"><span data-stu-id="d52eb-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="d52eb-121">В **Параметры конфиденциальности**выберите **общедоступный - всем пользователям в организации доступ к этому узлу**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d52eb-122">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="d52eb-123">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="d52eb-123">Here is your resulting configuration.</span></span>
  
![Защита базового уровня для общедоступного сайта группы SharePoint Online.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="d52eb-125">Частный</span><span class="sxs-lookup"><span data-stu-id="d52eb-125">Private</span></span>

<span data-ttu-id="d52eb-126">Чтобы создать базовый сайт группы SharePoint Online с условиями доступа и разрешениями, предусмотренными для частного сайта:</span><span class="sxs-lookup"><span data-stu-id="d52eb-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="d52eb-p104">Войдите в портал Office 365 с использованием учетной записи, которая также будет использоваться для администрирования SharePoint Online сайта группы (администратору SharePoint Online). Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d52eb-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d52eb-129">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d52eb-130">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d52eb-131">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d52eb-132">В поле **имя узла**введите имя сайта частной группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="d52eb-133">В **поле Описание сайта группы** введите описание назначения сайта.</span><span class="sxs-lookup"><span data-stu-id="d52eb-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="d52eb-134">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d52eb-135">На **пользователей, которые вы хотите добавить?** области, в **Добавление участников**, введите имена учетных записей пользователей, имеющих доступ к этот сайт частной группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="d52eb-136">После добавления к узлу начальный набор элементов нажмите кнопку **Готово**</span><span class="sxs-lookup"><span data-stu-id="d52eb-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="d52eb-137">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="d52eb-137">Here is your resulting configuration.</span></span>
  
![Защита базового уровня для закрытого сайта группы SharePoint Online.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="d52eb-139">Конфиденциальные сайты группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d52eb-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="d52eb-140">Конфиденциальный сайт группы SharePoint Online — это изолированный сайт группы, разрешения на доступ к которому определяются членством в группах SharePoint, а не в группе Office 365, связанной с этим сайтом группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="d52eb-141">Есть два основных этапа создания изолированного сайта группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="d52eb-142">Этап 1. Создание изолированного сайта</span><span class="sxs-lookup"><span data-stu-id="d52eb-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="d52eb-143">Для создания изолированного сайта группы выполните следующее:</span><span class="sxs-lookup"><span data-stu-id="d52eb-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="d52eb-144">Определите группы SharePoint и уровни разрешений.</span><span class="sxs-lookup"><span data-stu-id="d52eb-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="d52eb-145">Определите набор групп доступа, которые будут членами групп SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d52eb-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="d52eb-146">Рекомендуемый набор групп доступа — один для участников сайта, средства просмотра сайтов и Администраторы сайта.</span><span class="sxs-lookup"><span data-stu-id="d52eb-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="d52eb-147">Определите, будете ли использовать группы, вложенные в группы доступа.</span><span class="sxs-lookup"><span data-stu-id="d52eb-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="d52eb-148">Ниже приведен пример рекомендуемой структуры группы и уровней разрешений.</span><span class="sxs-lookup"><span data-stu-id="d52eb-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="d52eb-149">**Группа SharePoint**</span><span class="sxs-lookup"><span data-stu-id="d52eb-149">**SharePoint group**</span></span>|<span data-ttu-id="d52eb-150">**Уровень разрешений**</span><span class="sxs-lookup"><span data-stu-id="d52eb-150">**Permission level**</span></span>|<span data-ttu-id="d52eb-151">**Группа доступа (примеры)**</span><span class="sxs-lookup"><span data-stu-id="d52eb-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d52eb-152">[имя сайта] Члены</span><span class="sxs-lookup"><span data-stu-id="d52eb-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="d52eb-153">Изменение</span><span class="sxs-lookup"><span data-stu-id="d52eb-153">Edit</span></span>  <br/> |<span data-ttu-id="d52eb-154">[имя сайта] Члены</span><span class="sxs-lookup"><span data-stu-id="d52eb-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="d52eb-155">[имя сайта] Посетители</span><span class="sxs-lookup"><span data-stu-id="d52eb-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="d52eb-156">Чтение</span><span class="sxs-lookup"><span data-stu-id="d52eb-156">Read</span></span>  <br/> |<span data-ttu-id="d52eb-157">[имя сайта] Средства просмотра</span><span class="sxs-lookup"><span data-stu-id="d52eb-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="d52eb-158">[имя сайта] Владельцы сайтов</span><span class="sxs-lookup"><span data-stu-id="d52eb-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="d52eb-159">Полный контроль</span><span class="sxs-lookup"><span data-stu-id="d52eb-159">Full control</span></span>  <br/> |<span data-ttu-id="d52eb-160">[имя сайта] "Администраторы"</span><span class="sxs-lookup"><span data-stu-id="d52eb-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="d52eb-p105">Группы SharePoint и уровни разрешений создаются по умолчанию для сайта группы. Необходимо определить имена групп доступа.</span><span class="sxs-lookup"><span data-stu-id="d52eb-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="d52eb-163">Для получения дополнительных сведений в процессе разработки просмотрите [Оформление изолированной SharePoint Online сайт группы](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="d52eb-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="d52eb-164">Этап 2. Развертывание изолированного сайта</span><span class="sxs-lookup"><span data-stu-id="d52eb-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="d52eb-165">Для развертывания изолированного сайта необходимо сперва выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="d52eb-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="d52eb-166">Определить, какие группы и учетные записи пользователей следует добавить к каждой группе доступа.</span><span class="sxs-lookup"><span data-stu-id="d52eb-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="d52eb-167">Создать группы доступа и добавить пользователя и членов группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="d52eb-168">Подробное описание действий содержатся в **шаге 1** развернуть [изолированной SharePoint Online сайт группы](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="d52eb-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="d52eb-169">Далее следует создать сайт группы SharePoint Online, следуя приведенным ниже инструкциям.</span><span class="sxs-lookup"><span data-stu-id="d52eb-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="d52eb-p106">Войдите в портал Office 365 с использованием учетной записи, которая также будет использоваться для администрирования SharePoint Online сайта группы (администратору SharePoint Online). Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d52eb-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d52eb-172">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d52eb-173">На вкладке **SharePoint** нового окна браузера нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d52eb-174">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d52eb-175">В поле **имя узла**введите имя сайта частной группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="d52eb-176">В поле **Описание сайта группы**введите дополнительное описание.</span><span class="sxs-lookup"><span data-stu-id="d52eb-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="d52eb-177">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d52eb-178">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="d52eb-179">С помощью действий, приведенных ниже, настройте разрешения на новом сайте группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d52eb-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="d52eb-p107">Определите имя участника-пользователя (UPN) для ИТ-администратора или другого человека, который будет обрабатывать запросы на получение доступа к сайту и отвечать на них (reginap@contoso.com — пример имени участника-пользователя). Напишите это имя участника-пользователя здесь: _________________________________________.</span><span class="sxs-lookup"><span data-stu-id="d52eb-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="d52eb-182">В панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="d52eb-183">В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="d52eb-184">На вкладке **разрешения** нового браузера щелкните **Параметры запроса доступа**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="d52eb-185">В диалоговом окне **Параметры запросов доступа** :</span><span class="sxs-lookup"><span data-stu-id="d52eb-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="d52eb-186">Снимите флажки **Разрешить членам для совместного использования сайтов и отдельных файлов и папок** и **Разрешить участникам приглашать других людей для группы участников сайта** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="d52eb-187">Введите имя участника-пользователя для ИТ-администратор из шага 1 в **отправлять все запросы на доступ**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="d52eb-188">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="d52eb-189">На вкладке **разрешения** в браузере выберите в списке **члены [имя сайта]** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="d52eb-190">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="d52eb-191">В диалоговом окне **общий доступ** введите имя вашей доступа группы участников сайта для этого сайта, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="d52eb-192">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="d52eb-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="d52eb-193">В списке выберите **владельцев [имя сайта]** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="d52eb-194">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="d52eb-195">В диалоговом окне **общий доступ** введите имя группы доступа администраторов сайтов для данного узла, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="d52eb-196">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="d52eb-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="d52eb-197">В списке выберите **посетители [имя сайта]** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="d52eb-198">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="d52eb-199">В диалоговом окне **общий доступ** введите имя группы доступа средства просмотра сайта для этого сайта, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="d52eb-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="d52eb-200">Закройте вкладку **разрешения** браузера.</span><span class="sxs-lookup"><span data-stu-id="d52eb-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="d52eb-201">Ознакомьтесь с результатами настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="d52eb-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="d52eb-202">**Владельцы [имя сайта]** группы SharePoint содержит группы доступ администраторов сайтов, в которых все участники иметь уровень разрешений **полного доступа** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="d52eb-203">**[Имя сайта] члены** группы SharePoint содержит группы участников сайта доступа, в которых все участники иметь уровень разрешений **Изменить** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="d52eb-204">**Посетители [имя сайта]** группы SharePoint содержит группу доступа средства просмотра сайтов, в которых все участники иметь уровень разрешений **Чтение** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="d52eb-205">Отключается возможность элементы, чтобы пригласить других участников.</span><span class="sxs-lookup"><span data-stu-id="d52eb-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="d52eb-206">Включена возможность от членов запросить необходимые права доступа.</span><span class="sxs-lookup"><span data-stu-id="d52eb-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="d52eb-207">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="d52eb-207">Here is your resulting configuration.</span></span>
  
![Защита уровня конфиденциальности для изолированного сайта группы SharePoint Online.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="d52eb-209">Благодаря членству в одной из групп доступа участники сайта теперь могут совместно работать над ресурсами сайта, соблюдая требования безопасности.</span><span class="sxs-lookup"><span data-stu-id="d52eb-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="d52eb-210">Строго конфиденциальные сайты группы SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d52eb-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="d52eb-211">Строго конфиденциальный сайт группы SharePoint Online — это изолированный сайт группы, разрешения на доступ к которому определяются членством в группах SharePoint, а не в группе Office 365, связанной с этим сайтом группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="d52eb-212">Существует два основных этапа создания изолированного сайта группы для совместной работы, содержащего строго конфиденциальные данные.</span><span class="sxs-lookup"><span data-stu-id="d52eb-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="d52eb-213">Этап 1. Создание изолированного сайта</span><span class="sxs-lookup"><span data-stu-id="d52eb-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="d52eb-214">Для создания изолированного сайта группы выполните следующее:</span><span class="sxs-lookup"><span data-stu-id="d52eb-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="d52eb-215">Определите группы SharePoint и уровни разрешений.</span><span class="sxs-lookup"><span data-stu-id="d52eb-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="d52eb-216">Определите набор групп доступа, которые будут членами групп SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d52eb-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="d52eb-217">Рекомендуемый набор групп доступа — один для участников сайта, средства просмотра сайтов и Администраторы сайта.</span><span class="sxs-lookup"><span data-stu-id="d52eb-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="d52eb-218">Определите, будете ли использовать группы, вложенные в группы доступа.</span><span class="sxs-lookup"><span data-stu-id="d52eb-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="d52eb-219">Ниже приведен пример рекомендуемой структуры группы и уровней разрешений.</span><span class="sxs-lookup"><span data-stu-id="d52eb-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="d52eb-220">**Группа SharePoint**</span><span class="sxs-lookup"><span data-stu-id="d52eb-220">**SharePoint group**</span></span>|<span data-ttu-id="d52eb-221">**Уровень разрешений**</span><span class="sxs-lookup"><span data-stu-id="d52eb-221">**Permission level**</span></span>|<span data-ttu-id="d52eb-222">**Группа доступа (примеры)**</span><span class="sxs-lookup"><span data-stu-id="d52eb-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d52eb-223">[имя сайта] Члены</span><span class="sxs-lookup"><span data-stu-id="d52eb-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="d52eb-224">Изменение</span><span class="sxs-lookup"><span data-stu-id="d52eb-224">Edit</span></span>  <br/> |<span data-ttu-id="d52eb-225">[имя сайта] Члены</span><span class="sxs-lookup"><span data-stu-id="d52eb-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="d52eb-226">[имя сайта] Посетители</span><span class="sxs-lookup"><span data-stu-id="d52eb-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="d52eb-227">Чтение</span><span class="sxs-lookup"><span data-stu-id="d52eb-227">Read</span></span>  <br/> |<span data-ttu-id="d52eb-228">[имя сайта] Средства просмотра</span><span class="sxs-lookup"><span data-stu-id="d52eb-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="d52eb-229">[имя сайта] Владельцы сайтов</span><span class="sxs-lookup"><span data-stu-id="d52eb-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="d52eb-230">Полный контроль</span><span class="sxs-lookup"><span data-stu-id="d52eb-230">Full control</span></span>  <br/> |<span data-ttu-id="d52eb-231">[имя сайта] "Администраторы"</span><span class="sxs-lookup"><span data-stu-id="d52eb-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="d52eb-p108">Группы SharePoint и уровни разрешений создаются по умолчанию для сайта группы. Необходимо определить имена групп доступа.</span><span class="sxs-lookup"><span data-stu-id="d52eb-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="d52eb-234">Для получения дополнительных сведений в процессе разработки просмотрите [Оформление изолированной SharePoint Online сайт группы](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="d52eb-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="d52eb-235">Этап 2. Развертывание изолированного сайта</span><span class="sxs-lookup"><span data-stu-id="d52eb-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="d52eb-236">Для развертывания изолированного сайта необходимо сперва выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="d52eb-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="d52eb-237">Определить пользователя и членов каждой из групп доступа.</span><span class="sxs-lookup"><span data-stu-id="d52eb-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="d52eb-238">Создать группы доступа и добавить пользователя и членов группы.</span><span class="sxs-lookup"><span data-stu-id="d52eb-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="d52eb-239">Создать изолированный сайт группы, для которого используются группы доступа.</span><span class="sxs-lookup"><span data-stu-id="d52eb-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="d52eb-240">Подробное описание процедуры в разделе [Развертывание изолированного SharePoint Online сайт группы](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="d52eb-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="d52eb-241">Ниже приведены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="d52eb-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="d52eb-242">**Владельцы [имя сайта]** группы SharePoint содержит группы доступ администраторов сайтов, в которых все участники иметь уровень разрешений **полного доступа** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="d52eb-243">**[Имя сайта] члены** группы SharePoint содержит группы участников сайта доступа, в которых все участники иметь уровень разрешений **Изменить** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="d52eb-244">**Посетители [имя сайта]** группы SharePoint содержит группу доступа средства просмотра сайтов, в которых все участники иметь уровень разрешений **Чтение** .</span><span class="sxs-lookup"><span data-stu-id="d52eb-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="d52eb-245">Отключается возможность элементы, чтобы пригласить других участников.</span><span class="sxs-lookup"><span data-stu-id="d52eb-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="d52eb-246">Возможность от членов запросить доступ отключен.</span><span class="sxs-lookup"><span data-stu-id="d52eb-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="d52eb-247">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="d52eb-247">Here is your resulting configuration.</span></span>
  
![Защита уровня строгой конфиденциальности для изолированного сайта группы SharePoint Online.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="d52eb-249">Благодаря членству в одной из групп доступа участники сайта теперь могут совместно работать над ресурсами сайта, соблюдая требования безопасности.</span><span class="sxs-lookup"><span data-stu-id="d52eb-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="d52eb-250">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="d52eb-250">Next step</span></span>

[<span data-ttu-id="d52eb-251">Защита файлов SharePoint Online с помощью Office 365 метки и защиты от потери данных</span><span class="sxs-lookup"><span data-stu-id="d52eb-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="d52eb-252">See Also</span><span class="sxs-lookup"><span data-stu-id="d52eb-252">See Also</span></span>

[<span data-ttu-id="d52eb-253">Безопасность сайтов и файлов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d52eb-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="d52eb-254">Защита сайтов SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="d52eb-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="d52eb-255">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="d52eb-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="d52eb-256">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="d52eb-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




