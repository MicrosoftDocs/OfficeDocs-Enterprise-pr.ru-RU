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
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "Сводка: Создание и настройка SharePoint Online сайты рабочих групп для различных уровнях защита информации."
ms.openlocfilehash: f015ce8d7c91d02ce5dc0a7791ba22a53bc2933f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="10a42-103">Развертывание сайтов SharePoint Online для три уровня защиты</span><span class="sxs-lookup"><span data-stu-id="10a42-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="10a42-104">**Сводка:** Создание и настройка SharePoint Online сайты рабочих групп для различных уровнях защита информации.</span><span class="sxs-lookup"><span data-stu-id="10a42-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="10a42-p101">В этой статье приводятся инструкции по разработке и развертыванию сайтов групп SharePoint Online с базовым, конфиденциальным и строго конфиденциальным уровнями защиты. Дополнительные сведения об этих трех уровнях защиты см. в статье [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) (Защита сайтов и файлов SharePoint Online).</span><span class="sxs-lookup"><span data-stu-id="10a42-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="10a42-107">Сайты групп SharePoint Online с базовым уровнем защиты</span><span class="sxs-lookup"><span data-stu-id="10a42-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="10a42-p102">Базовый уровень защиты распространяется на частные и общедоступные сайты групп. Обнаруживать общедоступные сайты групп и получать к ним доступ может любой пользователь в организации. Обнаруживать частные сайты и получать к ним доступ могут только участники группы Office 365, связанной с сайтом группы. Оба этих типа сайтов групп позволяют участникам предоставлять доступ к сайту другим пользователям.</span><span class="sxs-lookup"><span data-stu-id="10a42-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="10a42-112">Открытый</span><span class="sxs-lookup"><span data-stu-id="10a42-112">Public</span></span>

<span data-ttu-id="10a42-113">Чтобы создать сайт группы SharePoint Online с базовым уровнем защиты и общим доступом и разрешениями, выполните приведенные далее действия.</span><span class="sxs-lookup"><span data-stu-id="10a42-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="10a42-p103">Войдите в портал Office 365 с использованием учетной записи, которая также будет использоваться для администрирования SharePoint Online сайта группы (администратору SharePoint Online). Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="10a42-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="10a42-116">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="10a42-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="10a42-117">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="10a42-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="10a42-118">На странице **Создание сайта** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="10a42-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="10a42-119">В поле **Имя сайта** введите имя для открытого сайта группы.</span><span class="sxs-lookup"><span data-stu-id="10a42-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="10a42-120">В поле **Описание сайта группы** введите описание назначения сайта.</span><span class="sxs-lookup"><span data-stu-id="10a42-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="10a42-121">В **Параметры конфиденциальности**выберите **общедоступный - всем пользователям в организации доступ к этому узлу**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="10a42-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="10a42-122">В области **Who do you want to add?** (Кого нужно добавить?) нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="10a42-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="10a42-123">Ниже показана результирующая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="10a42-123">Here is your resulting configuration.</span></span>
  
![Защита базового уровня для общедоступного сайта группы SharePoint Online.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="10a42-125">Private</span><span class="sxs-lookup"><span data-stu-id="10a42-125">Private</span></span>

<span data-ttu-id="10a42-126">Чтобы создать сайт группы SharePoint Online с базовым уровнем защиты и закрытым доступом и разрешениями, выполните приведенные далее действия.</span><span class="sxs-lookup"><span data-stu-id="10a42-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="10a42-p104">Войдите в портал Office 365 с использованием учетной записи, которая также будет использоваться для администрирования SharePoint Online сайта группы (администратору SharePoint Online). Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="10a42-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="10a42-129">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="10a42-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="10a42-130">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="10a42-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="10a42-131">На странице **Создание сайта** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="10a42-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="10a42-132">В поле **Имя сайта** введите имя для частного сайта группы.</span><span class="sxs-lookup"><span data-stu-id="10a42-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="10a42-133">В **поле Описание сайта группы** введите описание назначения сайта.</span><span class="sxs-lookup"><span data-stu-id="10a42-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="10a42-134">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="10a42-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="10a42-135">В области **Who do you want to add?** (Кого нужно добавить?) в поле **Добавить участников** введите имена учетных записей пользователей, имеющих доступ к этому частному сайту группы.</span><span class="sxs-lookup"><span data-stu-id="10a42-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="10a42-136">После добавления к узлу начальный набор элементов нажмите кнопку **Готово**</span><span class="sxs-lookup"><span data-stu-id="10a42-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="10a42-137">Ниже показана результирующая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="10a42-137">Here is your resulting configuration.</span></span>
  
![Защита базового уровня для закрытого сайта группы SharePoint Online.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="10a42-139">Сайты групп SharePoint Online с конфиденциальным уровнем защиты</span><span class="sxs-lookup"><span data-stu-id="10a42-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="10a42-140">Конфиденциальный сайт группы SharePoint Online — это изолированный сайт группы, разрешения на доступ к которому определяются членством в группах SharePoint, а не в группе Office 365, связанной с этим сайтом группы.</span><span class="sxs-lookup"><span data-stu-id="10a42-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="10a42-141">Есть два основных этапа создания изолированного сайта группы.</span><span class="sxs-lookup"><span data-stu-id="10a42-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="10a42-142">Этап 1. Создание изолированного сайта</span><span class="sxs-lookup"><span data-stu-id="10a42-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="10a42-143">Чтобы разработать изолированный сайт группы, необходимо определить:</span><span class="sxs-lookup"><span data-stu-id="10a42-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="10a42-144">Определите группы SharePoint и уровни разрешений.</span><span class="sxs-lookup"><span data-stu-id="10a42-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="10a42-145">Определите набор групп доступа, которые будут членами групп SharePoint.</span><span class="sxs-lookup"><span data-stu-id="10a42-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="10a42-146">Рекомендуемый набор групп доступа — один для участников сайта, средства просмотра сайтов и Администраторы сайта.</span><span class="sxs-lookup"><span data-stu-id="10a42-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="10a42-147">Будут ли использоваться вложенные группы внутри групп доступа.</span><span class="sxs-lookup"><span data-stu-id="10a42-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="10a42-148">Например, рекомендуемая структура групп и уровни разрешений выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="10a42-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="10a42-149">**Группа SharePoint**</span><span class="sxs-lookup"><span data-stu-id="10a42-149">**SharePoint group**</span></span>|<span data-ttu-id="10a42-150">**Уровень разрешений**</span><span class="sxs-lookup"><span data-stu-id="10a42-150">**Permission level**</span></span>|<span data-ttu-id="10a42-151">**Группа доступа (примеры)**</span><span class="sxs-lookup"><span data-stu-id="10a42-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="10a42-152">[имя сайта] — участники</span><span class="sxs-lookup"><span data-stu-id="10a42-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="10a42-153">Правка</span><span class="sxs-lookup"><span data-stu-id="10a42-153">Edit</span></span>  <br/> |<span data-ttu-id="10a42-154">[имя сайта] — участники</span><span class="sxs-lookup"><span data-stu-id="10a42-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="10a42-155">[имя сайта] — посетители</span><span class="sxs-lookup"><span data-stu-id="10a42-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="10a42-156">Чтение</span><span class="sxs-lookup"><span data-stu-id="10a42-156">Read</span></span>  <br/> |<span data-ttu-id="10a42-157">[имя сайта] — посетители</span><span class="sxs-lookup"><span data-stu-id="10a42-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="10a42-158">[имя сайта] — владельцы</span><span class="sxs-lookup"><span data-stu-id="10a42-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="10a42-159">Полный доступ</span><span class="sxs-lookup"><span data-stu-id="10a42-159">Full control</span></span>  <br/> |<span data-ttu-id="10a42-160">[имя сайта] — администраторы</span><span class="sxs-lookup"><span data-stu-id="10a42-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="10a42-p105">Группы и уровни разрешений SharePoint создаются по умолчанию для сайта группы. Необходимо определить имена групп доступа.</span><span class="sxs-lookup"><span data-stu-id="10a42-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="10a42-163">Сведения о процессе разработки см. в статье [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md) (Разработка изолированного сайта группы SharePoint Online).</span><span class="sxs-lookup"><span data-stu-id="10a42-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="10a42-164">Шаг 2. Развертывание изолированного сайта</span><span class="sxs-lookup"><span data-stu-id="10a42-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="10a42-165">Для развертывания изолированного сайта сначала необходимо:</span><span class="sxs-lookup"><span data-stu-id="10a42-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="10a42-166">определить учетные записи пользователей и группы пользователей для добавления в каждую группу доступа;</span><span class="sxs-lookup"><span data-stu-id="10a42-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="10a42-167">создать группы доступа и добавить пользователей и членов групп.</span><span class="sxs-lookup"><span data-stu-id="10a42-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="10a42-168">Подробные инструкции см. в разделе **Этап 1** статьи [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md) (Развертывание изолированного сайта группы SharePoint Online).</span><span class="sxs-lookup"><span data-stu-id="10a42-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="10a42-169">Далее следует создать сайт группы SharePoint Online, следуя приведенным ниже инструкциям.</span><span class="sxs-lookup"><span data-stu-id="10a42-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="10a42-p106">Войдите в портал Office 365 с использованием учетной записи, которая также будет использоваться для администрирования SharePoint Online сайта группы (администратору SharePoint Online). Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="10a42-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="10a42-172">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="10a42-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="10a42-173">На вкладке **SharePoint** нового окна браузера нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="10a42-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="10a42-174">На странице **Создание сайта** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="10a42-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="10a42-175">В поле **Имя сайта** введите имя для частного сайта группы.</span><span class="sxs-lookup"><span data-stu-id="10a42-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="10a42-176">В поле **Описание сайта группы**введите дополнительное описание.</span><span class="sxs-lookup"><span data-stu-id="10a42-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="10a42-177">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="10a42-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="10a42-178">В области **Who do you want to add?** (Кого нужно добавить?) нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="10a42-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="10a42-179">На новом сайте группы SharePoint Online настройте разрешения, выполнив описанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="10a42-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="10a42-p107">Определите имя участника-пользователя (UPN) для ИТ-администратора или другого человека, который будет обрабатывать запросы на получение доступа к сайту и отвечать на них (reginap@contoso.com — пример имени участника-пользователя). Напишите это имя участника-пользователя здесь: _________________________________________.</span><span class="sxs-lookup"><span data-stu-id="10a42-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="10a42-182">В панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="10a42-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="10a42-183">В области **Разрешения для сайта** щелкните **Дополнительные параметры разрешений**.</span><span class="sxs-lookup"><span data-stu-id="10a42-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="10a42-184">На новой вкладке браузера **Разрешения** щелкните **Параметры запроса доступа**.</span><span class="sxs-lookup"><span data-stu-id="10a42-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="10a42-185">В диалоговом окне **Параметры запросов доступа**:</span><span class="sxs-lookup"><span data-stu-id="10a42-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="10a42-186">Снимите флажки **Разрешить участникам совместный доступ к этому сайту, а также отдельным файлам и папкам** и **Разрешить участникам приглашать других пользователей в группу участников сайта**.</span><span class="sxs-lookup"><span data-stu-id="10a42-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="10a42-187">В поле **Отправлять все запросы на доступ** введите имя UPN ИТ-администратора из шага 1.</span><span class="sxs-lookup"><span data-stu-id="10a42-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="10a42-188">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="10a42-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="10a42-189">На вкладке браузера **Разрешения** в списке выберите **[имя сайта] — участники**.</span><span class="sxs-lookup"><span data-stu-id="10a42-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="10a42-190">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="10a42-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="10a42-191">В диалоговом окне **общий доступ** введите имя вашей доступа группы участников сайта для этого сайта, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="10a42-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="10a42-192">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="10a42-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="10a42-193">В списке выберите **владельцев [имя сайта]** .</span><span class="sxs-lookup"><span data-stu-id="10a42-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="10a42-194">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="10a42-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="10a42-195">В диалоговом окне **общий доступ** введите имя группы доступа администраторов сайтов для данного узла, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="10a42-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="10a42-196">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="10a42-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="10a42-197">В списке выберите **посетители [имя сайта]** .</span><span class="sxs-lookup"><span data-stu-id="10a42-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="10a42-198">**Пользователи и группы**нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="10a42-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="10a42-199">В диалоговом окне **общий доступ** введите имя группы доступа средства просмотра сайта для этого сайта, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="10a42-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="10a42-200">Закройте вкладку браузера **Разрешения**.</span><span class="sxs-lookup"><span data-stu-id="10a42-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="10a42-201">Ознакомьтесь с результатами настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="10a42-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="10a42-202">Группа SharePoint **[имя сайта] — владельцы** содержит группу доступа администраторов сайта, в которой все участники имеют уровень разрешений **Полный доступ**.</span><span class="sxs-lookup"><span data-stu-id="10a42-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="10a42-203">Группа SharePoint **[имя сайта] — участники** содержит группу доступа участников сайта, в которой все участники имеют уровень разрешений **Изменение**.</span><span class="sxs-lookup"><span data-stu-id="10a42-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="10a42-204">Группа SharePoint **[имя сайта] — посетители** содержит группу доступа посетителей сайта, в которой все участники имеют уровень разрешений **Чтение**.</span><span class="sxs-lookup"><span data-stu-id="10a42-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="10a42-205">Для участников отключена возможность приглашать других участников.</span><span class="sxs-lookup"><span data-stu-id="10a42-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="10a42-206">Для пользователей, не являющихся участниками, включена возможность запроса доступа.</span><span class="sxs-lookup"><span data-stu-id="10a42-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="10a42-207">Ниже показана результирующая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="10a42-207">Here is your resulting configuration.</span></span>
  
![Защита уровня конфиденциальности для изолированного сайта группы SharePoint Online.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="10a42-209">Благодаря членству в одной из групп доступа участники сайта теперь могут безопасно работать с ресурсами сайта.</span><span class="sxs-lookup"><span data-stu-id="10a42-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="10a42-210">Сайты групп SharePoint Online со строго конфиденциальным уровнем защиты</span><span class="sxs-lookup"><span data-stu-id="10a42-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="10a42-211">Сайт группы SharePoint Online со строго конфиденциальным уровнем защиты является изолированным сайтом группы. Это означает, что управление разрешениями осуществляется за счет членства в группах SharePoint, а не членства в группе Office 365, связанной с сайтом группы.</span><span class="sxs-lookup"><span data-stu-id="10a42-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="10a42-212">Создание изолированного сайта для строго конфиденциальных данных и совместной работы выполняется в два основных этапа.</span><span class="sxs-lookup"><span data-stu-id="10a42-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="10a42-213">Шаг 1. Разработка изолированного сайта</span><span class="sxs-lookup"><span data-stu-id="10a42-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="10a42-214">Чтобы разработать изолированный сайт группы, необходимо определить:</span><span class="sxs-lookup"><span data-stu-id="10a42-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="10a42-215">Определите группы SharePoint и уровни разрешений.</span><span class="sxs-lookup"><span data-stu-id="10a42-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="10a42-216">Определите набор групп доступа, которые будут членами групп SharePoint.</span><span class="sxs-lookup"><span data-stu-id="10a42-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="10a42-217">Рекомендуемый набор групп доступа — один для участников сайта, средства просмотра сайтов и Администраторы сайта.</span><span class="sxs-lookup"><span data-stu-id="10a42-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="10a42-218">Будут ли использоваться вложенные группы внутри групп доступа.</span><span class="sxs-lookup"><span data-stu-id="10a42-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="10a42-219">Например, рекомендуемая структура групп и уровни разрешений выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="10a42-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="10a42-220">**Группа SharePoint**</span><span class="sxs-lookup"><span data-stu-id="10a42-220">**SharePoint group**</span></span>|<span data-ttu-id="10a42-221">**Уровень разрешений**</span><span class="sxs-lookup"><span data-stu-id="10a42-221">**Permission level**</span></span>|<span data-ttu-id="10a42-222">**Группа доступа (примеры)**</span><span class="sxs-lookup"><span data-stu-id="10a42-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="10a42-223">[имя сайта] — участники</span><span class="sxs-lookup"><span data-stu-id="10a42-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="10a42-224">Правка</span><span class="sxs-lookup"><span data-stu-id="10a42-224">Edit</span></span>  <br/> |<span data-ttu-id="10a42-225">[имя сайта] — участники</span><span class="sxs-lookup"><span data-stu-id="10a42-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="10a42-226">[имя сайта] — посетители</span><span class="sxs-lookup"><span data-stu-id="10a42-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="10a42-227">Чтение</span><span class="sxs-lookup"><span data-stu-id="10a42-227">Read</span></span>  <br/> |<span data-ttu-id="10a42-228">[имя сайта] — посетители</span><span class="sxs-lookup"><span data-stu-id="10a42-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="10a42-229">[имя сайта] — владельцы</span><span class="sxs-lookup"><span data-stu-id="10a42-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="10a42-230">Полный доступ</span><span class="sxs-lookup"><span data-stu-id="10a42-230">Full control</span></span>  <br/> |<span data-ttu-id="10a42-231">[имя сайта] — администраторы</span><span class="sxs-lookup"><span data-stu-id="10a42-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="10a42-p108">Группы и уровни разрешений SharePoint создаются по умолчанию для сайта группы. Необходимо определить имена групп доступа.</span><span class="sxs-lookup"><span data-stu-id="10a42-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="10a42-234">Сведения о процессе разработки см. в статье [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md) (Разработка изолированного сайта группы SharePoint Online).</span><span class="sxs-lookup"><span data-stu-id="10a42-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="10a42-235">Шаг 2. Развертывание изолированного сайта</span><span class="sxs-lookup"><span data-stu-id="10a42-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="10a42-236">Для развертывания изолированного сайта необходимо сперва выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="10a42-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="10a42-237">Определить пользователя и членов каждой из групп доступа.</span><span class="sxs-lookup"><span data-stu-id="10a42-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="10a42-238">Создать группы доступа и добавить пользователя и членов группы.</span><span class="sxs-lookup"><span data-stu-id="10a42-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="10a42-239">Создать изолированный сайт группы, для которого используются группы доступа.</span><span class="sxs-lookup"><span data-stu-id="10a42-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="10a42-240">Подробные инструкции см. в статье [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md) (Развертывание изолированного сайта группы SharePoint Online).</span><span class="sxs-lookup"><span data-stu-id="10a42-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="10a42-241">Ниже приведены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="10a42-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="10a42-242">Группа SharePoint **[имя сайта] — владельцы** содержит группу доступа администраторов сайта, в которой все участники имеют уровень разрешений **Полный доступ**.</span><span class="sxs-lookup"><span data-stu-id="10a42-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="10a42-243">Группа SharePoint **[имя сайта] — участники** содержит группу доступа участников сайта, в которой все участники имеют уровень разрешений **Изменение**.</span><span class="sxs-lookup"><span data-stu-id="10a42-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="10a42-244">Группа SharePoint **[имя сайта] — посетители** содержит группу доступа посетителей сайта, в которой все участники имеют уровень разрешений **Чтение**.</span><span class="sxs-lookup"><span data-stu-id="10a42-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="10a42-245">Для участников отключена возможность приглашать других участников.</span><span class="sxs-lookup"><span data-stu-id="10a42-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="10a42-246">Для пользователей, не являющихся участниками, отключена возможность запроса доступа.</span><span class="sxs-lookup"><span data-stu-id="10a42-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="10a42-247">Ниже показана результирующая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="10a42-247">Here is your resulting configuration.</span></span>
  
![Защита уровня строгой конфиденциальности для изолированного сайта группы SharePoint Online.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="10a42-249">Благодаря членству в одной из групп доступа участники сайта теперь могут совместно работать над ресурсами сайта, соблюдая требования безопасности.</span><span class="sxs-lookup"><span data-stu-id="10a42-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="10a42-250">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="10a42-250">Next step</span></span>

[<span data-ttu-id="10a42-251">Защита файлов SharePoint Online с помощью Office 365 метки и защиты от потери данных</span><span class="sxs-lookup"><span data-stu-id="10a42-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="10a42-252">См. также</span><span class="sxs-lookup"><span data-stu-id="10a42-252">See Also</span></span>

[<span data-ttu-id="10a42-253">Безопасность сайтов и файлов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="10a42-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="10a42-254">Защита сайтов SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="10a42-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="10a42-255">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="10a42-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="10a42-256">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="10a42-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




