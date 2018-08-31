---
title: Создание сайтов групп в среде разработки и тестирования для политической кампании
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/21/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: Сводка. Сведения о том, как создавать общедоступные, частные, конфиденциальные и строго конфиденциальные сайты групп SharePoint Online в среде разработки и тестирования для политической кампании.
ms.openlocfilehash: 03e73a540d1a92d20446d8e12066df87bd179293
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915264"
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="87f45-103">Создание сайтов групп в среде разработки и тестирования для политической кампании</span><span class="sxs-lookup"><span data-stu-id="87f45-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="87f45-104">**Сводка.** Сведения о том, как создавать общедоступные, частные, конфиденциальные и строго конфиденциальные сайты групп SharePoint Online в среде разработки и тестирования для политической кампании.</span><span class="sxs-lookup"><span data-stu-id="87f45-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="87f45-p101">Инструкции из этой статьи позволят создать среду разработки и тестирования, которая включает четыре разных типа сайтов групп SharePoint Online для решения [Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md). Эти сайты подробно описаны в 10-й статье под названием **SharePoint и OneDrive для бизнеса**.</span><span class="sxs-lookup"><span data-stu-id="87f45-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="87f45-107">Этап 1. Создание среды разработки и тестирования для политической кампании</span><span class="sxs-lookup"><span data-stu-id="87f45-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="87f45-108">Сначала создайте подписки, пользователей и группы, следуя инструкциям из статьи [Настройка групп и пользователей в случае среды разработки и тестирования для политической кампании](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="87f45-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="87f45-109">Этап 2. Создание меток Office 365</span><span class="sxs-lookup"><span data-stu-id="87f45-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="87f45-110">На этом этапе вы создадите метки разных уровней защиты для папок документов на сайтах групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="87f45-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="87f45-p102">Если необходимо, войдите на портал Office 365 с использованием учетных данных учетной записи глобального администратора пробной подписки. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="87f45-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="87f45-113">На вкладке **Домашняя страница Microsoft Office** щелкните плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="87f45-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="87f45-114">На новой вкладке браузера **Центр администрирования Office** выберите **Центры администрирования > Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="87f45-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="87f45-115">На новой вкладке браузера **Главная — безопасность и соответствие требованиям** выберите **Классификации > Метки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="87f45-116">В области **Главная > Метки** нажмите кнопку **Создать метку**.</span><span class="sxs-lookup"><span data-stu-id="87f45-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="87f45-117">В области **Назовите метку** введите **Внутренний**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="87f45-118">В области **Параметры метки** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="87f45-119">В области **Проверьте параметры** нажмите **Создать эту метку**, а затем — кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="87f45-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="87f45-120">Повторите действия 5–8 для следующих меток:</span><span class="sxs-lookup"><span data-stu-id="87f45-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="87f45-121">Private</span><span class="sxs-lookup"><span data-stu-id="87f45-121">Private</span></span>
    
  - <span data-ttu-id="87f45-122">Конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="87f45-122">Sensitive</span></span>
    
  - <span data-ttu-id="87f45-123">Строго конфиденциально</span><span class="sxs-lookup"><span data-stu-id="87f45-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="87f45-124">В области **Главная > Метки** щелкните **Опубликовать метки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="87f45-125">В области **Выберите метки для публикации** щелкните **Выберите метки для публикации**.</span><span class="sxs-lookup"><span data-stu-id="87f45-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="87f45-126">В области **Выбор меток** нажмите кнопку **Добавить** и выберите все четыре метки.</span><span class="sxs-lookup"><span data-stu-id="87f45-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="87f45-127">Нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="87f45-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="87f45-128">В области **Выберите метки для публикации** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="87f45-129">В области **Выберите расположения** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="87f45-130">В области **Назовите политику** введите **Кампания** в поле **Название**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="87f45-131">В области **Проверьте параметры** последовательно нажмите кнопки **Опубликовать метки** и **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="87f45-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="87f45-132">Этап 3. Создание сайтов групп SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="87f45-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="87f45-133">На этом этапе мы создадим и настроим сайты групп SharePoint Online для политической кампании, соответствующие четырем типам сайтов групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="87f45-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="87f45-134">Общий сайт группы для кампании</span><span class="sxs-lookup"><span data-stu-id="87f45-134">Campaign wide team site</span></span>

<span data-ttu-id="87f45-135">Чтобы создать общедоступный сайт группы SharePoint Online с базовым уровнем защиты, выполните приведенные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="87f45-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="87f45-136">Если необходимо, в браузере на локальном компьютере войдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="87f45-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="87f45-137">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="87f45-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="87f45-138">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="87f45-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="87f45-139">На странице **Создайте сайт** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="87f45-140">В поле **Имя сайта** введите **Общий сайт кампании**.</span><span class="sxs-lookup"><span data-stu-id="87f45-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="87f45-141">В поле **Описание сайта группы** введите **Общий сайт SharePoint для кампании**.</span><span class="sxs-lookup"><span data-stu-id="87f45-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="87f45-142">В разделе **Параметры конфиденциальности** выберите **Общедоступная группа: все в организации имеют доступ к этому сайту** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="87f45-143">В области **Кого вы хотите добавить?** нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="87f45-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="87f45-144">Затем настройте папку документов на сайте группы "Общий сайт кампании" для использования метки "Внутренний".</span><span class="sxs-lookup"><span data-stu-id="87f45-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="87f45-145">На вкладке **Общий сайт кампании — главная** в браузере выберите **Документы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="87f45-146">Щелкните значок параметров и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="87f45-147">В разделе **Разрешения и управление** нажмите кнопку **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="87f45-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="87f45-148">В разделе **Параметры — применение метки** выберите метку **Внутренний** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="87f45-149">Сайт группы "Проект кампании 1"</span><span class="sxs-lookup"><span data-stu-id="87f45-149">Campaign project 1 team site</span></span>

<span data-ttu-id="87f45-150">Чтобы создать частный сайт группы SharePoint Online с базовым уровнем защиты для проекта в рамках кампании, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="87f45-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="87f45-151">Если необходимо, в браузере на локальном компьютере войдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="87f45-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="87f45-152">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="87f45-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="87f45-153">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="87f45-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="87f45-154">На странице **Создайте сайт** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="87f45-155">В поле **Имя сайта** введите **Проект кампании 1**. </span><span class="sxs-lookup"><span data-stu-id="87f45-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="87f45-156">В поле **Описание сайта группы** введите **Сайт SharePoint для проекта кампании 1**.</span><span class="sxs-lookup"><span data-stu-id="87f45-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="87f45-157">В разделе **Параметры конфиденциальности** выберите **Закрытая группа: только участники имеют доступ к этому сайту** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="87f45-158">В области **Кого вы хотите добавить?** нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="87f45-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="87f45-159">Затем настройте папку документов на сайте группы "Проект кампании 1" на использование метки "Частный".</span><span class="sxs-lookup"><span data-stu-id="87f45-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="87f45-160">На вкладке **Проект кампании 1 — главная** в браузере выберите **Документы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="87f45-161">Щелкните значок параметров и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="87f45-162">В разделе **Разрешения и управление** нажмите кнопку **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="87f45-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="87f45-163">В разделе **Параметры — применение метки** выберите метку **Частный** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="87f45-164">Сайт группы "Маркетинг кампании"</span><span class="sxs-lookup"><span data-stu-id="87f45-164">Campaign marketing team site</span></span>

<span data-ttu-id="87f45-165">Чтобы создать изолированный сайт группы SharePoint Online с уровнем защиты для конфиденциальных данных в случае маркетинговых ресурсов кампании, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="87f45-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="87f45-166">В браузере на локальном компьютере войдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="87f45-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="87f45-167">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="87f45-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="87f45-168">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="87f45-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="87f45-169">На странице **Создайте сайт** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="87f45-170">В поле **Имя сайта группы** введите **Маркетинг кампании**.</span><span class="sxs-lookup"><span data-stu-id="87f45-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="87f45-171">В поле **Описание сайта группы** введите **Сайт SharePoint для маркетингового отдела кампании (конфиденциальный)**.</span><span class="sxs-lookup"><span data-stu-id="87f45-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="87f45-172">В разделе **Параметры конфиденциальности** выберите **Закрытая группа: только участники имеют доступ к этому сайту** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="87f45-173">В области **Кого вы хотите добавить?** нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="87f45-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="87f45-174">Перейдите к новой вкладке **Маркетинг кампании** в браузере, а затем на панели инструментов нажмите значок параметров и выберите **Разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="87f45-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="87f45-175">В области **Разрешения для сайта** щелкните **Параметры дополнительных разрешений**.</span><span class="sxs-lookup"><span data-stu-id="87f45-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="87f45-176">На новой вкладке браузера **Разрешения** щелкните **Параметры запросов на доступ**.</span><span class="sxs-lookup"><span data-stu-id="87f45-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="87f45-177">В диалоговом окне **Параметры запросов на доступ** снимите флажки **Разрешить участникам совместный доступ к этому сайту, а также отдельным файлам и папкам** и **Разрешить участникам приглашать других пользователей в группу участников сайта**, введите **ITAdmin1@**<your organization name> **.onmicrosoft.com** в поле **Отправлять все запросы на доступ**, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="87f45-178">Выберите в списке пункт **Маркетинг кампании — участники**.</span><span class="sxs-lookup"><span data-stu-id="87f45-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="87f45-179">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="87f45-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="87f45-180">В диалоговом окне **Общий доступ** введите **Старший и стратегический персонал**, выберите группу и нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="87f45-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="87f45-181">Повторите этапы 14 и 15 для группы **Персонал отдела аналитики** и учетной записи **Обычная1**.</span><span class="sxs-lookup"><span data-stu-id="87f45-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="87f45-182">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="87f45-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="87f45-183">Выберите в списке пункт **Маркетинг кампании — владельцы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="87f45-184">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="87f45-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="87f45-185">В диалоговом окне **Общий доступ** введите **ИТ-персонал**, выберите группу и нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="87f45-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="87f45-186">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="87f45-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="87f45-187">Закройте вкладку **Пользователи и группы** в браузере, перейдите на вкладку **Маркетинг кампании — главная** в браузере и закройте область **Разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="87f45-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="87f45-188">Ниже приведены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="87f45-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="87f45-189">Группа SharePoint **Маркетинг кампании — участники** содержит только группу **Старший и стратегический персонал** (которая включает учетные записи "Кандидат", "НачальникШтаба" и "Стратег1"), группу **Маркетинг кампании** (которая включает учетную запись глобального администратора), группу **Персонал отдела аналитики** (которая включает учетную запись "ОбработчикДанных1") и учетную запись пользователя **Обычная1**.</span><span class="sxs-lookup"><span data-stu-id="87f45-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="87f45-190">Группа SharePoint **Маркетинг кампании — владельцы** содержит только группу **ИТ-персонал**, которая включает только учетные записи ITAdmin1 и ITAdmin2.</span><span class="sxs-lookup"><span data-stu-id="87f45-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="87f45-191">Группа SharePoint **Маркетинг кампании — посетители** не содержит ни групп, ни учетных записей.</span><span class="sxs-lookup"><span data-stu-id="87f45-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="87f45-192">Участники не могут менять разрешения на уровне сайта (это могут делать только члены группы **Маркетинг кампании — владельцы**).</span><span class="sxs-lookup"><span data-stu-id="87f45-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="87f45-193">У других учетных записей нет доступа к сайту и его ресурсам, но они могут запрашивать доступ к сайту. При этом в почтовый ящик пользователя "ИТ-администратор1" отправляется электронное сообщение.</span><span class="sxs-lookup"><span data-stu-id="87f45-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="87f45-194">Теперь настройте папку документов на сайте группы "Маркетинг кампании" на использование метки "Конфиденциальный".</span><span class="sxs-lookup"><span data-stu-id="87f45-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="87f45-195">На вкладке **Маркетинг кампании — главная** в браузере выберите **Документы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="87f45-196">Щелкните значок параметров и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="87f45-197">В разделе **Разрешения и управление** нажмите кнопку **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="87f45-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="87f45-198">В разделе **Параметры — применение метки** выберите метку **Конфиденциальный** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="87f45-p103">Настройте политику защиты от потери данных (DLP), которая уведомляет пользователей, когда они предоставляют доступ к документу на сайте группы SharePoint Online с меткой "Конфиденциальный" внешним пользователям. Такая политика будет применяться к ресурсам на сайте "Маркетинг кампании".</span><span class="sxs-lookup"><span data-stu-id="87f45-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="87f45-201">На вкладке браузера **Домашняя страница Microsoft Office** щелкните плитку **Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="87f45-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="87f45-202">На новой вкладке **Безопасность и соответствие требованиям** выберите **Защита от потери данных > Политика**.</span><span class="sxs-lookup"><span data-stu-id="87f45-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="87f45-203">В области **Защита от потери данных** нажмите кнопку **+ Создание политики**.</span><span class="sxs-lookup"><span data-stu-id="87f45-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="87f45-204">В области **Начать с шаблона или создать настраиваемую политику** выберите **Настраиваемая**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="87f45-205">В области **Назовите политику** введите **Сайты групп SharePoint Online с меткой "Конфиденциальный"** в поле **Имя**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="87f45-206">В области **Выберите расположения** щелкните **Позволить мне выбрать расположения** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="87f45-207">В списке расположений отключите параметры **Электронная почта Exchange** и **Учетные записи OneDrive**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="87f45-208">В области **Выберите тип содержимого, которое вы хотите защитить** щелкните ссылку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="87f45-209">В области **Выбрать типы содержимого для защиты** выберите **Добавить** в раскрывающемся списке, а затем выберите **Метки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="87f45-210">В области **Метки** нажмите кнопку **+ Добавить**, укажите метку **Конфиденциальный** и последовательно нажмите кнопки **Добавить** > **Готово**.</span><span class="sxs-lookup"><span data-stu-id="87f45-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="87f45-211">В области **Выбрать типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="87f45-212">В области **Customize the types of sensitive info you want to protect** (Настройка типов защищаемых конфиденциальных сведений) нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="87f45-213">В области **What do you want to do if we detect sensitive info?** (Что делать при обнаружении конфиденциальной информации?) щелкните **Customize the tip and email** (Настроить подсказки и уведомления по электронной почте).</span><span class="sxs-lookup"><span data-stu-id="87f45-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="87f45-214">В области **Customize policy tips and email notifications** (Настройка подсказок политики и уведомления по электронной почте) щелкните **Customize the policy tip text** (Настроить текст подсказки политики).</span><span class="sxs-lookup"><span data-stu-id="87f45-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="87f45-215">В текстовом поле введите или вставьте следующее:</span><span class="sxs-lookup"><span data-stu-id="87f45-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="87f45-p104">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="87f45-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="87f45-219">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="87f45-220">В области **Что делать при обнаружении конфиденциальной информации?** снимите флажки **Запретить пользователям делиться контентом и ограничить доступ к совместно используемому содержимому**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="87f45-221">В области **Включить политику или сначала протестировать ее?** выберите пункт **Да, включить ее сразу**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="87f45-222">В области **Проверка параметров** нажмите **Создать**, а затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="87f45-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="87f45-223">Сайт группы "Стратегия кампании"</span><span class="sxs-lookup"><span data-stu-id="87f45-223">Campaign strategy team site</span></span>

<span data-ttu-id="87f45-224">Чтобы создать изолированный сайт группы SharePoint Online с уровнем защиты строго конфиденциальных данных для стратегических ресурсов кампании, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="87f45-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="87f45-225">Если необходимо, в браузере на локальном компьютере войдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="87f45-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="87f45-226">В списке плиток выберите **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="87f45-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="87f45-227">На новой вкладке **SharePoint** в браузере щелкните **+ Создать сайт**.</span><span class="sxs-lookup"><span data-stu-id="87f45-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="87f45-228">На странице **Создайте сайт** щелкните **Сайт группы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="87f45-229">В поле **Имя сайта группы** введите **Стратегия кампании**.</span><span class="sxs-lookup"><span data-stu-id="87f45-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="87f45-230">В поле **Описание сайта группы** введите **Сайт SharePoint для стратегии кампании (строго конфиденциальный)**.</span><span class="sxs-lookup"><span data-stu-id="87f45-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="87f45-231">В разделе **Параметры конфиденциальности** выберите **Закрытая группа: только участники имеют доступ к этому сайту** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="87f45-232">В области **Кого вы хотите добавить?** нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="87f45-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="87f45-233">На новой вкладке **Стратегия кампании** браузера нажмите значок параметров на панели инструментов и выберите **Разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="87f45-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="87f45-234">В области **Разрешения для сайта** щелкните **Параметры дополнительных разрешений**.</span><span class="sxs-lookup"><span data-stu-id="87f45-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="87f45-235">На новой вкладке браузера **Разрешения** щелкните **Параметры запросов на доступ**.</span><span class="sxs-lookup"><span data-stu-id="87f45-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="87f45-236">В диалоговом окне **Параметры запросов на доступ** снимите флажки **Разрешить участникам совместный доступ к этому сайту, а также отдельным файлам и папкам** и **Разрешить участникам приглашать других пользователей в группу участников сайта** (все три флажка должны быть сняты) и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="87f45-237">Выберите в списке пункт **Стратегия кампании — участники**.</span><span class="sxs-lookup"><span data-stu-id="87f45-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="87f45-238">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="87f45-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="87f45-239">В диалоговом окне **Общий доступ** введите **Старший и стратегический персонал**, выберите группу и нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="87f45-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="87f45-240">Выберите в списке группу **Стратегия кампании — владельцы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="87f45-241">На странице **Пользователи и группы** нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="87f45-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="87f45-242">В диалоговом окне **Общий доступ** введите **ИТ-персонал**, выберите группу и нажмите **Общий доступ**.</span><span class="sxs-lookup"><span data-stu-id="87f45-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="87f45-243">Нажмите кнопку "Назад" в браузере.</span><span class="sxs-lookup"><span data-stu-id="87f45-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="87f45-244">Закройте вкладку **Пользователи и группы** в браузере, перейдите на вкладку **Стратегия кампании — главная** в браузере и закройте область **Разрешения для сайта**.</span><span class="sxs-lookup"><span data-stu-id="87f45-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="87f45-245">Ниже приведены результаты настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="87f45-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="87f45-246">Группа SharePoint **Стратегия кампании — участники** содержит только группу **Старший и стратегический персонал** (которая включает только учетные записи "Кандидат", "НачальникШтаба" и "Стратег1") и группу **Стратегия кампании** (которая включает только учетную запись глобального администратора).
</span><span class="sxs-lookup"><span data-stu-id="87f45-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="87f45-247">Группа SharePoint **Стратегия кампании — владельцы** содержит только группу **ИТ-персонал**, которая включает только учетные записи ITAdmin1 и ITAdmin2.</span><span class="sxs-lookup"><span data-stu-id="87f45-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="87f45-248">Группа SharePoint **Стратегия кампании — посетители** не содержит ни групп, ни учетных записей.</span><span class="sxs-lookup"><span data-stu-id="87f45-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="87f45-249">Участники не могут менять разрешения на уровне сайта (это могут делать только члены группы **Стратегия кампании — владельцы**).</span><span class="sxs-lookup"><span data-stu-id="87f45-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="87f45-p105">Другие учетные записи пользователей не могут получать доступ к сайту и его ресурсам, а также запрашивать доступ к нему. Дополнительные разрешения для сайта должен задавать глобальный администратор или участник группы **Стратегия кампании — владельцы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="87f45-252">Затем настройте папку документов на сайте стратегической группы кампании на использование метки "Строго конфиденциальный".</span><span class="sxs-lookup"><span data-stu-id="87f45-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="87f45-253">На вкладке **Стратегия кампании — главная** в браузере выберите **Документы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="87f45-254">Щелкните значок параметров и выберите **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="87f45-255">В разделе **Разрешения и управление** нажмите кнопку **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="87f45-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="87f45-256">В разделе **Параметры — применение метки** выберите метку **Строго конфиденциальный** и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="87f45-p106">Настройте политику защиты от потери данных, которая блокирует попытки предоставить внешним пользователям доступ к документу на сайте группы SharePoint Online с меткой "Строго конфиденциальный". Такая политика будет применяться к ресурсам на сайте "Стратегия кампании".</span><span class="sxs-lookup"><span data-stu-id="87f45-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="87f45-259">Если необходимо, в браузере на локальном компьютере войдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)), используя учетную запись с ролью администратора безопасности или администратора организации.</span><span class="sxs-lookup"><span data-stu-id="87f45-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="87f45-260">На вкладке браузера **Домашняя страница Microsoft Office** щелкните плитку **Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="87f45-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="87f45-261">На новой вкладке **Безопасность и соответствие требованиям** выберите **Защита от потери данных > Политика**.</span><span class="sxs-lookup"><span data-stu-id="87f45-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="87f45-262">В области **Защита от потери данных** нажмите кнопку **+ Создание политики**.</span><span class="sxs-lookup"><span data-stu-id="87f45-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="87f45-263">В области **Начать с шаблона или создать настраиваемую политику** выберите **Настраиваемая**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="87f45-264">В области **Назовите политику** введите **Сайты групп SharePoint Online с меткой "Строго конфиденциальный"** в поле **Имя**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="87f45-265">В области **Выберите расположения** щелкните **Позволить мне выбрать расположения** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="87f45-266">В списке расположений отключите параметры **Электронная почта Exchange** и **Учетные записи OneDrive**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="87f45-267">В области **Выберите тип содержимого, которое вы хотите защитить** щелкните ссылку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="87f45-268">В области **Выбрать типы содержимого для защиты** выберите **Добавить** в раскрывающемся списке, а затем выберите **Метки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="87f45-269">В области **Метки** нажмите кнопку **+ Добавить**, выберите метку **Строго конфиденциальный**, нажмите **Добавить**, а затем нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="87f45-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="87f45-270">В области **Выбрать типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="87f45-271">В области **Customize the types of sensitive info you want to protect** (Настройка типов защищаемых конфиденциальных сведений) нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="87f45-272">В области **What do you want to do if we detect sensitive info?** (Что делать при обнаружении конфиденциальной информации?) щелкните **Customize the tip and email** (Настроить подсказки и уведомления по электронной почте).</span><span class="sxs-lookup"><span data-stu-id="87f45-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="87f45-273">В области **Customize policy tips and email notifications** (Настройка подсказок политики и уведомления по электронной почте) щелкните **Customize the policy tip text** (Настроить текст подсказки политики).</span><span class="sxs-lookup"><span data-stu-id="87f45-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="87f45-274">В текстовом поле введите или вставьте следующее:</span><span class="sxs-lookup"><span data-stu-id="87f45-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="87f45-p107">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="87f45-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="87f45-278">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="87f45-279">В области **Что делать при обнаружении конфиденциальной информации?** выберите **Требовать коммерческое обоснование для переопределения**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="87f45-280">В области **Включить политику или сначала протестировать ее?** выберите пункт **Да, включить ее сразу**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="87f45-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="87f45-281">В области **Проверка параметров** нажмите **Создать**, а затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="87f45-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="87f45-282">Воспользуйтесь инструкциями из статьи [Активация Azure RMS в Центре администрирования Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="87f45-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="87f45-283">Затем настройте для Azure Information Protection новую политику области и вложенную метку для защиты и разрешений, выполнив следующие действия:</span><span class="sxs-lookup"><span data-stu-id="87f45-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="87f45-p108">Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="87f45-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="87f45-286">Перейдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), открыв отдельную вкладку браузера.</span><span class="sxs-lookup"><span data-stu-id="87f45-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="87f45-287">Если вы настраиваете Azure Information Protection впервые, ознакомьтесь с этими [инструкциями](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="87f45-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="87f45-288">На панели списка выберите **Все службы**, введите **information**, а затем выберите **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="87f45-288">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>

5. <span data-ttu-id="87f45-289">Выберите **Метки**.</span><span class="sxs-lookup"><span data-stu-id="87f45-289">Click **Labels**.</span></span>
    
6. <span data-ttu-id="87f45-290">Щелкните правой кнопкой мыши метку **Строго конфиденциально** и выберите элемент **Добавить подчин. метку**.</span><span class="sxs-lookup"><span data-stu-id="87f45-290">Right-click the **Highly Confidential** label, and then click **Add a sub-label**.</span></span>
    
7. <span data-ttu-id="87f45-291">Введите **СтратегияКампании** в поле **Имя** и **Метка для документов на сайте группы "Стратегия кампании"** в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="87f45-291">Type **CampaignStrategy** in **Name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
8. <span data-ttu-id="87f45-292">В разделе **Задайте разрешения для документов и электронных писем, имеющих эту метку** нажмите кнопку **Защитить**.</span><span class="sxs-lookup"><span data-stu-id="87f45-292">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
9. <span data-ttu-id="87f45-293">В разделе **Защита** выберите элемент **Azure (облачный ключ)**.</span><span class="sxs-lookup"><span data-stu-id="87f45-293">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
10. <span data-ttu-id="87f45-294">В колонке **Защита** в разделе **Параметры защиты** нажмите кнопку **+ Добавить разрешения**.</span><span class="sxs-lookup"><span data-stu-id="87f45-294">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
11. <span data-ttu-id="87f45-295">Перейдите к колонке **Добавление разрешений** и выберите **+ Обзор каталога** в разделе **Укажите пользователей и группы**.</span><span class="sxs-lookup"><span data-stu-id="87f45-295">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
12. <span data-ttu-id="87f45-296">В области **Пользователи и группы AAD** выберите группу **Старший и стратегический персонал** и нажмите кнопку **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="87f45-296">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
13. <span data-ttu-id="87f45-297">В разделе **Выбрать из предустановленных разрешений или задать пользовательские** выберите вариант **Пользовательские**, а затем установите флажки **Просмотреть права**, **Изменить контент**, **Сохранить**, **Ответить** и **Ответить всем**.</span><span class="sxs-lookup"><span data-stu-id="87f45-297">Under **Choose permissions from the preset or set custom**, click **Custom**, and then click the **View Rights**, **Edit Content**, **Save**, **Reply**, and **Reply all** check boxes.</span></span>
    
14. <span data-ttu-id="87f45-298">Дважды нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-298">Click **OK** twice.</span></span>
    
15. <span data-ttu-id="87f45-299">В колонке **Подчиненная метка** нажмите кнопку **Сохранить**, а затем щелкните **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-299">On the **Sub-label** blade, click **Save**, and then click **OK**.</span></span>

16. <span data-ttu-id="87f45-300">В колонке **Azure Information Protection** щелкните элементы **Политики > + Добавить политику**.</span><span class="sxs-lookup"><span data-stu-id="87f45-300">On the **Azure Information protection** blade, click **Policies > + Add a new policy**.</span></span>
    
17. <span data-ttu-id="87f45-301">Введите **СтратегияКампании** в поле **Имя** и **Документы на сайте группы "Стратегия кампании"** в поле **Описание**.</span><span class="sxs-lookup"><span data-stu-id="87f45-301">Type **CampaignStrategy** in **Name** and **Documents in the Campaign strategy team site** in **Description**.</span></span>
    
18. <span data-ttu-id="87f45-302">Щелкните **Выберите, к каким пользователям или группам будет применяться эта политика > Пользователи или группы**, а затем выберите **Старший и стратегический персонал**.</span><span class="sxs-lookup"><span data-stu-id="87f45-302">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
19. <span data-ttu-id="87f45-303">Щелкните **Выбрать > ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-303">Click **Select > OK**.</span></span>

20. <span data-ttu-id="87f45-p109">Выберите элемент **Добавить или удалить метки**. На панели **Политики: добавление и удаление меток** нажмите **СтратегияКампании**, а затем — **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-p109">Click **Add or remove labels**. In the **Policy: Add or remove labels** pane, click **CampaignStrategy**, and then click **OK**.</span></span>   

21. <span data-ttu-id="87f45-306">Нажмите кнопку **Сохранить**, а затем — **ОК**.</span><span class="sxs-lookup"><span data-stu-id="87f45-306">Click **Save**, and then click **OK**.</span></span>
  
<span data-ttu-id="87f45-307">Теперь вы можете создавать документы на этих четырех сайтах и тестировать доступ к ним с помощью различных учетных записей.</span><span class="sxs-lookup"><span data-stu-id="87f45-307">You are now ready to begin creating documents in these four sites and test access to them with various user accounts.</span></span> 
  
<span data-ttu-id="87f45-308">Чтобы защитить документ с помощью Azure Information Protection и новой метки, необходимо [установить клиент Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) на тестовом компьютере, установить набор Office, скачав его на портале Office 365, а затем выполнить вход из Microsoft Word с использованием учетной записи в группе **Старший и стратегический персонал** пробной подписки.</span><span class="sxs-lookup"><span data-stu-id="87f45-308">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="87f45-309">См. также</span><span class="sxs-lookup"><span data-stu-id="87f45-309">See Also</span></span>

[<span data-ttu-id="87f45-310">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="87f45-310">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="87f45-311">Настройка групп и пользователей в случае среды разработки и тестирования для политической кампании</span><span class="sxs-lookup"><span data-stu-id="87f45-311">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="87f45-312">Руководства по лабораториям тестирования (TLG) для освоения облачных решений</span><span class="sxs-lookup"><span data-stu-id="87f45-312">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="87f45-313">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="87f45-313">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




