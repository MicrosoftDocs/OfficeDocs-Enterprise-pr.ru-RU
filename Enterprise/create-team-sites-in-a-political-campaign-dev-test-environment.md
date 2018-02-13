---
title: "Создание сайтов группы в среде разработки и тестирования для политической кампании"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Сводка: Создание общедоступные, частный, конфиденциальные и конфиденциальными SharePoint Online сайтов группы в среде разработки и тестирования политических кампании."
ms.openlocfilehash: d1515d2534713de41c16640d0008b1f8146ab300
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="7be13-103">Создание сайтов группы в среде разработки и тестирования для политической кампании</span><span class="sxs-lookup"><span data-stu-id="7be13-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="7be13-104">**Сводка:** Создайте общедоступные, частный, конфиденциальные и конфиденциальными SharePoint Online сайтов группы в среде разработки и тестирования политических кампании.</span><span class="sxs-lookup"><span data-stu-id="7be13-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="7be13-p101">Использовать инструкции из статьи в этой статье для создания среды разработки или тестирования, которая включает в себя четыре различных типов веб-сайтов SharePoint Online групп [Руководство по безопасности корпорации Майкрософт для политических по сбору средств, некоммерческим организациями и другие гибкой организации](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) решение. Эти сайты подробно описаны в разделе 10, под названием **SharePoint и OneDrive для бизнеса**.</span><span class="sxs-lookup"><span data-stu-id="7be13-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="7be13-107">Этап 1. Создание среды разработки и тестирования для политической кампании</span><span class="sxs-lookup"><span data-stu-id="7be13-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="7be13-108">Во-первых следуйте инструкциям в [Настройка групп и пользователей в среде разработки и тестирования политических кампании](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) для создания подписок, пользователи и группы.</span><span class="sxs-lookup"><span data-stu-id="7be13-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="7be13-109">Этап 2. Создание меток Office 365</span><span class="sxs-lookup"><span data-stu-id="7be13-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="7be13-110">На этом этапе создается метки для разных уровнях безопасности для папок документов сайта SharePoint Online группы.</span><span class="sxs-lookup"><span data-stu-id="7be13-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="7be13-p102">При необходимости, войдите в портал Office 365 с использованием учетных данных учетной записи глобального администратора пробной подписки. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="7be13-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="7be13-113">Откройте вкладку **Microsoft Office для дома** и щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="7be13-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="7be13-114">В новую вкладку **Центр администрирования Office** обозревателя, выберите **центры администрирования > Безопасность &amp; соответствия**.</span><span class="sxs-lookup"><span data-stu-id="7be13-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="7be13-115">От нового **Home — безопасности &amp; соответствия** вкладки браузера, нажмите кнопку **классификаций > меток**.</span><span class="sxs-lookup"><span data-stu-id="7be13-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="7be13-116">Из **Домашняя страница > меток** области, нажмите кнопку **создать метку**.</span><span class="sxs-lookup"><span data-stu-id="7be13-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="7be13-117">В области **имя метки** **Внутренний**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="7be13-118">В области **Параметры метки** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="7be13-119">На панели **Проверьте параметры** нажмите кнопку **Создать в этом метки**и нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="7be13-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="7be13-120">Повторите действия 5–8 для следующих меток:</span><span class="sxs-lookup"><span data-stu-id="7be13-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="7be13-121">Частный</span><span class="sxs-lookup"><span data-stu-id="7be13-121">Private</span></span>
    
  - <span data-ttu-id="7be13-122">Конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="7be13-122">Sensitive</span></span>
    
  - <span data-ttu-id="7be13-123">Строго конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="7be13-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="7be13-124">Из **Домашняя страница > меток** области, нажмите кнопку **Опубликовать метки**.</span><span class="sxs-lookup"><span data-stu-id="7be13-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="7be13-125">В области **выбора меток для публикации** выберите **Выбор меток для публикации**.</span><span class="sxs-lookup"><span data-stu-id="7be13-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="7be13-126">В области **выберите метки** нажмите кнопку **Добавить** и выберите пункт все четыре метки.</span><span class="sxs-lookup"><span data-stu-id="7be13-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="7be13-127">Нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="7be13-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="7be13-128">В области **выбора меток для публикации** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="7be13-129">В области **выбора расположения** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="7be13-130">В области **Имя политики** введите **кампании** в поле **имя**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="7be13-131">В области **Проверьте параметры** нажмите кнопку **Опубликовать меток**и нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="7be13-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="7be13-132">Этап 3. Создание сайтов групп SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7be13-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="7be13-133">На этом этапе мы создадим и настроим сайты групп SharePoint Online для политической кампании, соответствующие четырем типам сайтов групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7be13-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="7be13-134">Общий сайт группы для кампании</span><span class="sxs-lookup"><span data-stu-id="7be13-134">Campaign wide team site</span></span>

<span data-ttu-id="7be13-135">Чтобы создать базовый общедоступный сайт группы SharePoint Online, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="7be13-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="7be13-136">В случае необходимости, используйте браузер на локальном компьютере и войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя свою учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="7be13-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="7be13-137">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="7be13-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="7be13-138">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="7be13-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="7be13-139">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="7be13-140">В поле **имя узла**введите **широкий кампании**.</span><span class="sxs-lookup"><span data-stu-id="7be13-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="7be13-141">В поле **Описание сайта группы**укажите **сайт SharePoint для всей кампании**.</span><span class="sxs-lookup"><span data-stu-id="7be13-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="7be13-142">В **Параметры конфиденциальности**выберите **общедоступный - всем пользователям в организации доступ к этому узлу**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7be13-143">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="7be13-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="7be13-144">Затем настройте папку документов на общем сайте группы на использование метки "Внутренний".</span><span class="sxs-lookup"><span data-stu-id="7be13-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="7be13-145">На вкладке **кампании всей домашней** браузера щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="7be13-146">Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="7be13-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="7be13-147">В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="7be13-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="7be13-148">**Применение параметров метки** **Внутренний**и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="7be13-149">Сайт группы "Проект кампании 1"</span><span class="sxs-lookup"><span data-stu-id="7be13-149">Campaign project 1 team site</span></span>

<span data-ttu-id="7be13-150">Чтобы создать базовый частный сайт группы SharePoint Online для проекта в рамках кампании, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="7be13-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="7be13-151">В случае необходимости, используйте браузер на локальном компьютере и войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя свою учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="7be13-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="7be13-152">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="7be13-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="7be13-153">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="7be13-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="7be13-154">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="7be13-155">В поле **имя узла**введите **кампании проект 1**.</span><span class="sxs-lookup"><span data-stu-id="7be13-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="7be13-156">В **поле Описание сайта группы** укажите **сайт SharePoint для проекта кампании 1**.</span><span class="sxs-lookup"><span data-stu-id="7be13-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="7be13-157">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7be13-158">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="7be13-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="7be13-159">Затем настройте папку документов на сайте группы "Проект кампании 1" на использование метки "Частный".</span><span class="sxs-lookup"><span data-stu-id="7be13-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="7be13-160">На вкладке **кампании Домашняя страница project 1** браузера щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="7be13-161">Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="7be13-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="7be13-162">В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="7be13-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="7be13-163">В поле **Применить параметры метки**выберите **частный**и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="7be13-164">Сайт группы "Маркетинг кампании"</span><span class="sxs-lookup"><span data-stu-id="7be13-164">Campaign marketing team site</span></span>

<span data-ttu-id="7be13-165">Чтобы создать изолированный сайт группы SharePoint Online на конфиденциальном уровне, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="7be13-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="7be13-166">С помощью браузера на локальном компьютере, выполните вход в портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя свою учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="7be13-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="7be13-167">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="7be13-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="7be13-168">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="7be13-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="7be13-169">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="7be13-170">В поле **имя сайта группы**введите **маркетинговые кампании**.</span><span class="sxs-lookup"><span data-stu-id="7be13-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="7be13-171">В поле **Описание сайта группы**укажите **сайт SharePoint для кампании, маркетинговые (с учетом)**.</span><span class="sxs-lookup"><span data-stu-id="7be13-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="7be13-172">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7be13-173">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="7be13-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="7be13-174">На вкладке **маркетинговые кампании** в браузере, в панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="7be13-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="7be13-175">В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="7be13-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="7be13-176">На новой вкладке **разрешения** в браузере нажмите кнопку **Параметры запроса доступа**.</span><span class="sxs-lookup"><span data-stu-id="7be13-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="7be13-177">В диалоговом окне **Параметры запроса доступа** снимите флажки **Разрешить членам для совместного использования сайтов и отдельных файлов и папок** и **Разрешить участникам приглашать других людей для группы участников сайта** введите **ITAdmin1 @** <your organization name> **. onmicrosoft.com** в **отправлять все запросы на доступ**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="7be13-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="7be13-178">Выберите в списке **участников маркетинговых кампаний (en)** .</span><span class="sxs-lookup"><span data-stu-id="7be13-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="7be13-179">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="7be13-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="7be13-180">В диалоговом окне **общий доступ** введите **старший и стратегического персонала**, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="7be13-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="7be13-181">Повторите шаги 14 и 15 для группы **аналитики персонала** и учетная запись пользователя **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="7be13-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="7be13-182">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="7be13-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="7be13-183">В списке выберите **владельцев маркетинговых кампаний (en)** .</span><span class="sxs-lookup"><span data-stu-id="7be13-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="7be13-184">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="7be13-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="7be13-185">В диалоговом окне **общий доступ** введите **ИТ-специалистов**, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="7be13-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="7be13-186">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="7be13-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="7be13-187">Закройте вкладку **людей и групп** в браузере, перейдите на вкладку **Дома маркетинговые кампании** в браузере, а затем закройте в области **разрешения для сайта** .</span><span class="sxs-lookup"><span data-stu-id="7be13-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="7be13-188">Ниже представлены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="7be13-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="7be13-189">Группа **Участников маркетингового кампании** SharePoint содержит только **старший и стратегического персонала** группе (содержащий учетные записи пользователей кандидата, ChiefOfStaff и Strategic1) **маркетинговой кампании** группы (который содержит Учетная запись пользователя глобального администратора), группа **персонала аналитики** (содержащий учетной записи пользователя DataScientist1) и учетная запись пользователя **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="7be13-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="7be13-190">**Маркетинговые кампании - владельцев** группы SharePoint содержит только группы **ИТ-специалистов** (который содержит только ITAdmin1 и ITAdmin2 учетные записи пользователей).</span><span class="sxs-lookup"><span data-stu-id="7be13-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="7be13-191">**Маркетинговые кампании - посетители** группы SharePoint не содержит групп или учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="7be13-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="7be13-192">Члены не могут изменять разрешения на уровне сайта (это может быть выполнено только члены группы **Владельцами маркетинговые кампании** ).</span><span class="sxs-lookup"><span data-stu-id="7be13-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="7be13-193">У других учетных записей нет доступа к сайту и его ресурсам, но они могут запрашивать доступ к сайту. При этом в почтовый ящик пользователя "ИТ-администратор1" отправляется электронное сообщение.</span><span class="sxs-lookup"><span data-stu-id="7be13-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="7be13-194">Теперь настройте папку документов на сайте группы "Маркетинг кампании" на использование метки "Конфиденциальный".</span><span class="sxs-lookup"><span data-stu-id="7be13-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="7be13-195">На вкладке **Маркетинговые кампании - Домашняя страница** браузера щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="7be13-196">Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="7be13-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="7be13-197">В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="7be13-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="7be13-198">В поле **Применить параметры метки**выберите **конфиденциальных**и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="7be13-p103">Настройте политику предотвращения (DLP) потери данных, которое уведомляет пользователей, если они совместное использование документов на сайте группы SharePoint Online с конфиденциальными метки за пределами организации. Эта политика защиты от потери данных будет применяться к ресурсам в сайт маркетинговых кампаний.</span><span class="sxs-lookup"><span data-stu-id="7be13-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="7be13-201">На вкладке **Microsoft Office для дома** в браузере выберите **безопасности &amp; соответствия** заголовков.</span><span class="sxs-lookup"><span data-stu-id="7be13-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="7be13-202">В новом **безопасности &amp; соответствия** в браузере, щелкните **защиту от потери данных > политики**.</span><span class="sxs-lookup"><span data-stu-id="7be13-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="7be13-203">На левой панели **защиту от потери данных** нажмите кнопку **+ Создать политику**.</span><span class="sxs-lookup"><span data-stu-id="7be13-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="7be13-204">В **Начать с шаблоном или создайте пользовательскую политику** области, выберите **настраиваемые**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="7be13-205">В области **Имя политики** введите **конфиденциальных метки SharePoint Online веб-сайтов групп** в поле **имя**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="7be13-206">На левой панели **Выберите расположение** нажмите кнопку **выбрать определенные расположения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="7be13-207">В списке расположений отключить расположения **учетных записей OneDrive** и **электронной почты Exchange** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7be13-208">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="7be13-209">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Добавить** , в раскрывающемся списке и нажмите кнопку **метки**.</span><span class="sxs-lookup"><span data-stu-id="7be13-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="7be13-210">В области **метки** нажмите кнопку **+ Добавить**, выберите **конфиденциальных** метку, нажмите кнопку **Добавить**и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="7be13-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="7be13-211">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="7be13-212">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="7be13-213">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, нажмите кнопку **Настройка подсказки и адрес электронной почты**.</span><span class="sxs-lookup"><span data-stu-id="7be13-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="7be13-214">В области **Настройка подсказок политики и уведомления по электронной почте** нажмите кнопку **Настройка текст подсказки политики**.</span><span class="sxs-lookup"><span data-stu-id="7be13-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="7be13-215">В текстовом поле введите или вставьте в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="7be13-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="7be13-p104">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="7be13-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="7be13-219">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="7be13-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="7be13-220">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, снимите флажок **Блокировать людей из общего доступа и ограничить доступ к общее содержимое** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="7be13-221">В **хотите ли вы включить действия политики или тестирования сначала?** области, нажмите кнопку **Да, включить немедленно**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="7be13-222">В области **Проверьте параметры** нажмите кнопку **Создать**и затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="7be13-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="7be13-223">Сайт стратегической группы кампании</span><span class="sxs-lookup"><span data-stu-id="7be13-223">Campaign strategy team site</span></span>

<span data-ttu-id="7be13-224">Чтобы создать изолированный сайт группы SharePoint Online на строго конфиденциальном уровне для стратегических ресурсов кампании, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="7be13-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="7be13-225">В случае необходимости, используйте браузер на локальном компьютере и войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя свою учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="7be13-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="7be13-226">В списке заголовков щелкните **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="7be13-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="7be13-227">На новой вкладке **SharePoint** в браузере нажмите кнопку **+ Создание сайта**.</span><span class="sxs-lookup"><span data-stu-id="7be13-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="7be13-228">На странице **создания сайта** щелкните **сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="7be13-229">В поле **имя сайта группы**введите **стратегии кампании**.</span><span class="sxs-lookup"><span data-stu-id="7be13-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="7be13-230">В поле **Описание сайта группы**укажите **сайт SharePoint для стратегии кампании (конфиденциальными)**.</span><span class="sxs-lookup"><span data-stu-id="7be13-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="7be13-231">В **Параметры конфиденциальности**, выберите **частный — только для членов можно получить доступ к этот сайт**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7be13-232">На **пользователей, которые вы хотите добавить?** области, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="7be13-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="7be13-233">На вкладке **стратегия кампании** в браузере, в панели инструментов щелкните значок параметры и нажмите кнопку **разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="7be13-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="7be13-234">В области **разрешения для сайта** выберите **Параметры дополнительные разрешения**.</span><span class="sxs-lookup"><span data-stu-id="7be13-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="7be13-235">На новой вкладке **разрешения** в браузере нажмите кнопку **Параметры запроса доступа**.</span><span class="sxs-lookup"><span data-stu-id="7be13-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="7be13-236">В диалоговом окне **Параметры запроса доступа** снимите флажок **Разрешить участникам совместного использования сайтов и отдельных файлов и папок** и **Разрешить участникам приглашать других людей для группы участников сайта** (, чтобы все три флажка), а затем нажмите кнопку ** Кнопки ОК**.</span><span class="sxs-lookup"><span data-stu-id="7be13-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="7be13-237">Выберите **стратегии кампании элементы** в списке.</span><span class="sxs-lookup"><span data-stu-id="7be13-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="7be13-238">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="7be13-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="7be13-239">В диалоговом окне **общий доступ** введите **старший и стратегического персонала**, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="7be13-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="7be13-240">В списке выберите **стратегии кампании владельцев** .</span><span class="sxs-lookup"><span data-stu-id="7be13-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="7be13-241">На странице " **пользователи и группы** " нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="7be13-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="7be13-242">В диалоговом окне **общий доступ** введите **ИТ-специалистов**, выберите его и нажмите кнопку **общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="7be13-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="7be13-243">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="7be13-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="7be13-244">Закройте вкладку **людей и групп** в браузере, перейдите на вкладку **Главная страница стратегии кампании** в браузере, а затем закройте в области **разрешения для сайта** .</span><span class="sxs-lookup"><span data-stu-id="7be13-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="7be13-245">Ниже представлены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="7be13-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="7be13-246">Группы SharePoint **Кампании стратегии — члены** содержит только **старший и стратегического персонала** группы (который содержит только кандидата, ChiefOfStaff и Strategic1 учетные записи пользователей) и **стратегии кампании** группы (который содержит только глобальный администратор учетной записи пользователя).</span><span class="sxs-lookup"><span data-stu-id="7be13-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="7be13-247">Группы SharePoint **Кампании стратегия владельцев** содержит только группы **ИТ-специалистов** (который содержит только ITAdmin1 и ITAdmin2 учетные записи пользователей).</span><span class="sxs-lookup"><span data-stu-id="7be13-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="7be13-248">Группы SharePoint **Кампании стратегия посетители** не содержит групп или учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="7be13-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="7be13-249">Члены не могут изменять разрешения на уровне сайта (это может быть выполнено только члены группы **Кампании стратегия владельцев** ).</span><span class="sxs-lookup"><span data-stu-id="7be13-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="7be13-p105">Другие учетные записи пользователей не удается доступ к узлу или его ресурсов или запросить доступ к сайту. Глобальный администратор или членом группы **Кампании стратегия владельцев** , необходимо выполнить дополнительные разрешения для сайта.</span><span class="sxs-lookup"><span data-stu-id="7be13-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="7be13-252">Затем настройте папку документов на сайте стратегической группы кампании на использование метки "Строго конфиденциальный".</span><span class="sxs-lookup"><span data-stu-id="7be13-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="7be13-253">На вкладке **Главная страница стратегии кампании** браузера щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="7be13-254">Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="7be13-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="7be13-255">В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="7be13-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="7be13-256">В поле **Применить параметры метки**выберите **Конфиденциальными**и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="7be13-p106">Настройте политику предотвращения потери данных, которое пользователи блоки при их совместное использование документов на сайте группы SharePoint Online с конфиденциальными метки за пределами организации. Эта политика защиты от потери данных будет применяться к ресурсам в сайт стратегической кампаний.</span><span class="sxs-lookup"><span data-stu-id="7be13-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="7be13-259">В случае необходимости, используйте браузер на локальном компьютере и войдите в портал Office 365 ([https://portal.office.com](https://portal.office.com)) с использованием учетной записи, имеющей роли безопасности администратора или администратора компании.</span><span class="sxs-lookup"><span data-stu-id="7be13-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="7be13-260">На вкладке **Microsoft Office для дома** в браузере выберите **безопасности &amp; соответствия** заголовков.</span><span class="sxs-lookup"><span data-stu-id="7be13-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="7be13-261">В новом **безопасности &amp; соответствия** в браузере, щелкните **защиту от потери данных > политики**.</span><span class="sxs-lookup"><span data-stu-id="7be13-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="7be13-262">На левой панели **защиту от потери данных** нажмите кнопку **+ Создать политику**.</span><span class="sxs-lookup"><span data-stu-id="7be13-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="7be13-263">В **Начать с шаблоном или создайте пользовательскую политику** области, выберите **настраиваемые**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="7be13-264">В области **Имя политики** введите **конфиденциальными метки SharePoint Online веб-сайтов групп** в поле **имя**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="7be13-265">На левой панели **Выберите расположение** нажмите кнопку **выбрать определенные расположения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7be13-266">В списке расположений отключить расположения **учетных записей OneDrive** и **электронной почты Exchange** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="7be13-267">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="7be13-268">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Добавить** , в раскрывающемся списке и нажмите кнопку **метки**.</span><span class="sxs-lookup"><span data-stu-id="7be13-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="7be13-269">На левой панели **метки** нажмите кнопку **+ Добавить**, выберите метку **Конфиденциальными** , нажмите кнопку **Добавить**и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="7be13-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="7be13-270">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="7be13-271">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="7be13-272">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, нажмите кнопку **Настройка подсказки и адрес электронной почты**.</span><span class="sxs-lookup"><span data-stu-id="7be13-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="7be13-273">В области **Настройка подсказок политики и уведомления по электронной почте** нажмите кнопку **Настройка текст подсказки политики**.</span><span class="sxs-lookup"><span data-stu-id="7be13-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="7be13-274">В текстовом поле введите или вставьте в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="7be13-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="7be13-p107">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="7be13-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="7be13-278">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="7be13-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="7be13-279">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, выберите **Требовать деловое обоснование для переопределения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="7be13-280">В **хотите ли вы включить действия политики или тестирования сначала?** области, нажмите кнопку **Да, включить немедленно**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7be13-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="7be13-281">В области **Проверьте параметры** нажмите кнопку **Создать**и затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="7be13-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="7be13-282">Используйте инструкции из статьи [Активировать Azure службы управления правами с помощью центра администрирования Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="7be13-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="7be13-283">Далее настройте защита информации Azure с новой областью видимости политики и вложенных метку для защиты и разрешения с помощью следующих действий:</span><span class="sxs-lookup"><span data-stu-id="7be13-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="7be13-p108">Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="7be13-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="7be13-286">Перейдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), открыв отдельную вкладку браузера.</span><span class="sxs-lookup"><span data-stu-id="7be13-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="7be13-287">Если вы настраиваете Azure Information Protection впервые, ознакомьтесь с этими [инструкциями](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="7be13-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="7be13-288">На панели списка выберите **Дополнительные службы**, введите **Информация**, а затем выберите **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="7be13-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="7be13-289">В колонке **Azure Information Protection**, щелкните последовательно элементы **Политики в области > + Добавить политику**.</span><span class="sxs-lookup"><span data-stu-id="7be13-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="7be13-290">В **имени политики** и **метки для документов на сайте рабочей группы стратегии кампании** в **поле Описание**введите **CampaignStrategy** .</span><span class="sxs-lookup"><span data-stu-id="7be13-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="7be13-291">Нажмите кнопку **выбрать, какие пользователи или группы получить эту политику > пользователей и групп**, а затем выберите **старший и стратегического персонала**.</span><span class="sxs-lookup"><span data-stu-id="7be13-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="7be13-292">Щелкните элементы **Выбрать > ОК**.</span><span class="sxs-lookup"><span data-stu-id="7be13-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="7be13-293">Для метки **Строго конфиденциально** щелкните последовательно многоточие (…) и элемент **Добавить подчин. метку**.</span><span class="sxs-lookup"><span data-stu-id="7be13-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="7be13-294">Введите имя подчиненной метки в поле **Имя** и описание метки в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="7be13-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="7be13-295">В разделе **Задайте разрешения для документов и электронных писем, имеющих эту метку** нажмите кнопку **Защитить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="7be13-296">В разделе **Защита** выберите элемент **Azure (облачный ключ)**.</span><span class="sxs-lookup"><span data-stu-id="7be13-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="7be13-297">В колонке **Защита** в разделе **Параметры защиты** нажмите кнопку **+ Добавить разрешения**.</span><span class="sxs-lookup"><span data-stu-id="7be13-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="7be13-298">Перейдите к колонке **Добавление разрешений** и выберите **+ Обзор каталога** в разделе **Укажите пользователей и группы**.</span><span class="sxs-lookup"><span data-stu-id="7be13-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="7be13-299">В области **AAD пользователей и групп** выберите **старший и стратегического персонала**и нажмите кнопку **выбрать**.</span><span class="sxs-lookup"><span data-stu-id="7be13-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="7be13-300">В разделе **Выбор разрешений из шаблона** снимите флажки **Печать**, **Копирование и извлечение контента** и **Переадресация**.</span><span class="sxs-lookup"><span data-stu-id="7be13-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="7be13-301">Дважды нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="7be13-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="7be13-302">В колонке **Подчиненная метка** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="7be13-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="7be13-303">Закройте колонку новой политики области.</span><span class="sxs-lookup"><span data-stu-id="7be13-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="7be13-304">На blade **Защита информации Azure - областью видимости политик** нажмите кнопку **Опубликовать**и нажмите кнопку **Да**.</span><span class="sxs-lookup"><span data-stu-id="7be13-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="7be13-305">Теперь вы можете создавать документы на этих четырех сайтах и тестировать доступ к ним с помощью различных учетных записей в пробной подписке.</span><span class="sxs-lookup"><span data-stu-id="7be13-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="7be13-306">Чтобы защитить документ с Azure защита информации и этой новой метки, необходимо [установить клиент защита информации Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) на тестовом компьютере, установка Office с портала Office 365 и войдите в из Microsoft Word с использованием учетной записи в ** Старший и стратегического персонала** группы пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="7be13-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7be13-307">См. также</span><span class="sxs-lookup"><span data-stu-id="7be13-307">See Also</span></span>

[<span data-ttu-id="7be13-308">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="7be13-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="7be13-309">Настройка групп и пользователей в среде разработки и тестирования политических кампаний (en)</span><span class="sxs-lookup"><span data-stu-id="7be13-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="7be13-310">Руководства по созданию сред разработки и тестирования облачных решений</span><span class="sxs-lookup"><span data-stu-id="7be13-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="7be13-311">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="7be13-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




