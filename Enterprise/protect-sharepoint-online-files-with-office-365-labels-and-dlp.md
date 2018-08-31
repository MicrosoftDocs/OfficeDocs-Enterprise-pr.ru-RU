---
title: Защита файлов SharePoint Online с помощью меток Office 365 и DLP
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: Сводка. Применяйте метки Office 365 и политики защиты от потери данных для сайтов групп SharePoint Online с различными уровнями защиты информации.
ms.openlocfilehash: 1e83f8c08dde55c22b7b9e8e6f9fe966c9fe9c02
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915784"
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="9c435-103">Защита файлов SharePoint Online с помощью меток Office 365 и DLP</span><span class="sxs-lookup"><span data-stu-id="9c435-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="9c435-104">**Сводка.** Применяйте метки Office 365 и политики защиты от потери данных для сайтов групп SharePoint Online с различными уровнями защиты информации.</span><span class="sxs-lookup"><span data-stu-id="9c435-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="9c435-p101">В этой статье описано создание и развертывание меток Office 365 и политик защиты от потери данных для базовых, конфиденциальных и строго конфиденциальных сайтов группы SharePoint Online. Дополнительные сведения об этих трех уровнях защиты см. в статье [Безопасность сайтов и файлов SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="9c435-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="how-this-works"></a><span data-ttu-id="9c435-107">Как это работает</span><span class="sxs-lookup"><span data-stu-id="9c435-107">How this works</span></span>
1. <span data-ttu-id="9c435-p102">Создайте нужные метки и опубликуйте их. Для их публикации может потребоваться до 12 часов.</span><span class="sxs-lookup"><span data-stu-id="9c435-p102">Create the desired labels and publish these. It can take up to 12 hours for these to be published.</span></span>
2. <span data-ttu-id="9c435-110">Для нужных сайтов SharePoint измените параметры библиотеки документов, чтобы присвоить метку к элементам в библиотеке.</span><span class="sxs-lookup"><span data-stu-id="9c435-110">For the desired SharePoint sites, edit the document library settings to apply a label to items in the library.</span></span>
3. <span data-ttu-id="9c435-111">Создайте политики защиты от потери данных, чтобы выполнять действия на основе меток.</span><span class="sxs-lookup"><span data-stu-id="9c435-111">Create DLP policies to take action based on the labels.</span></span>

<span data-ttu-id="9c435-p103">Когда пользователи добавляют документ в библиотеку, этот документ получает назначенную метку по умолчанию. При необходимости пользователи могут изменить метку. Если пользователь делится документом за пределами организации, служба защиты от потери данных проверяет, назначена ли метка, и выполняет действия, если политика защиты от потери данных соответствует метке. Служба защиты от потери данных также проверяет соответствие другим политикам, таким как защита файлов с номерами кредитных карт, если этот тип политики настроен.</span><span class="sxs-lookup"><span data-stu-id="9c435-p103">When users add a document to the library, the document will receive the assigned label by default. Users can change the label,if needed. When a user shares a document outside the organization, DLP will check to see if a label is assigned and take action if a DLP policy matches the label. DLP will look for other policy matches as well, such as protecting files with credit card numbers if this type of policy is configured.</span></span> 

## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="9c435-116">Метки Office 365 для сайтов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c435-116">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="9c435-117">Существует три этапа создания и назначения меток Office 365 для сайтов группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c435-117">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="9c435-118">Этап 1. Определение имен меток Office 365</span><span class="sxs-lookup"><span data-stu-id="9c435-118">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="9c435-p104">На этом этапе нужно определить названия меток Office 365 для четырех уровней защиты информации, применяемых к сайтам группы SharePoint Online. В приведенной ниже таблице перечислены рекомендуемые имена для каждого уровня.</span><span class="sxs-lookup"><span data-stu-id="9c435-p104">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="9c435-121">**Уровень защиты сайта группы SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="9c435-121">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="9c435-122">**Имя метки**</span><span class="sxs-lookup"><span data-stu-id="9c435-122">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9c435-123">Базовый общедоступный</span><span class="sxs-lookup"><span data-stu-id="9c435-123">Baseline-Public</span></span>  <br/> |<span data-ttu-id="9c435-124">Внутренний общедоступный</span><span class="sxs-lookup"><span data-stu-id="9c435-124">Internal public</span></span>  <br/> |
|<span data-ttu-id="9c435-125">Базовый частный</span><span class="sxs-lookup"><span data-stu-id="9c435-125">Baseline-Private</span></span>  <br/> |<span data-ttu-id="9c435-126">Private</span><span class="sxs-lookup"><span data-stu-id="9c435-126">Private</span></span>  <br/> |
|<span data-ttu-id="9c435-127">Конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="9c435-127">Sensitive</span></span>  <br/> |<span data-ttu-id="9c435-128">Конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="9c435-128">Sensitive</span></span>  <br/> |
|<span data-ttu-id="9c435-129">Строго конфиденциально</span><span class="sxs-lookup"><span data-stu-id="9c435-129">Highly Confidential</span></span>  <br/> |<span data-ttu-id="9c435-130">Строго конфиденциально</span><span class="sxs-lookup"><span data-stu-id="9c435-130">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="9c435-131">Этап 2. Создание меток Office 365</span><span class="sxs-lookup"><span data-stu-id="9c435-131">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="9c435-132">На этом этапе нужно создать и опубликовать определенные метки для разных уровней защиты информации.</span><span class="sxs-lookup"><span data-stu-id="9c435-132">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="9c435-133">Создать метки можно с помощью Microsoft PowerShell или Центра администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="9c435-133">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="9c435-134">Создание меток Office 365 в Центре администрирования Office 365</span><span class="sxs-lookup"><span data-stu-id="9c435-134">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="9c435-p105">Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="9c435-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="9c435-137">На вкладке **Домашняя страница Microsoft Office** щелкните плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="9c435-137">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="9c435-138">На новой вкладке браузера **Центр администрирования Office** выберите **Центры администрирования > Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="9c435-138">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="9c435-139">На новой вкладке браузера **Главная — безопасность и соответствие требованиям** выберите **Классификации > Метки**.</span><span class="sxs-lookup"><span data-stu-id="9c435-139">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="9c435-140">В области **Главная > Метки** щелкните **Создать метку**.</span><span class="sxs-lookup"><span data-stu-id="9c435-140">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="9c435-141">В области **Задайте имя для метки** введите название метки, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-141">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="9c435-142">В области **Параметры метки** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-142">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="9c435-143">В области **Проверьте параметры** нажмите **Создать эту метку**, а затем — кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="9c435-143">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="9c435-144">Повторите действия 5–8, чтобы создать дополнительные метки.</span><span class="sxs-lookup"><span data-stu-id="9c435-144">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="9c435-145">Создание меток Office 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c435-145">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="9c435-146">[Подключитесь к Центру безопасности и соответствия требованиям Office 365 с помощью удаленного сеанса PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) и укажите данные учетной записи, которой назначена роль администратора безопасности или роль администратора организации.</span><span class="sxs-lookup"><span data-stu-id="9c435-146">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="9c435-147">Заполните список имен меток, а затем выполните эти команды в командной строке PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9c435-147">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="9c435-148">Для публикации новых меток Office 365 выполните действия, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="9c435-148">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="9c435-149">В области **Главная > Метки** Центра безопасности и соответствия требованиям выберите **Опубликовать метки**.</span><span class="sxs-lookup"><span data-stu-id="9c435-149">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="9c435-150">В области **Выбор меток для публикации** щелкните **Выбрать метки для публикации**.</span><span class="sxs-lookup"><span data-stu-id="9c435-150">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="9c435-151">В области **Выбор меток** нажмите кнопку **Добавить** и выберите все четыре метки.</span><span class="sxs-lookup"><span data-stu-id="9c435-151">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="9c435-152">Нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="9c435-152">Click **Done**.</span></span>
    
5. <span data-ttu-id="9c435-153">В области **Выберите метки для публикации** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-153">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="9c435-154">В области **Выбор расположений** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-154">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="9c435-155">В области **Укажите имя для политики** введите название для своего набора меток в поле **Имя**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-155">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="9c435-156">В области **Проверьте настройки** выберите **Опубликовать метки** и нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="9c435-156">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="9c435-157">Этап 3. Применение меток Office 365 к сайтам SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c435-157">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="9c435-158">Инструкции по применению меток Office 365 к папкам документов, размещенным на сайтах группы SharePoint Online, приведены ниже.</span><span class="sxs-lookup"><span data-stu-id="9c435-158">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="9c435-159">На вкладке браузера **Главная (Microsoft Office)** щелкните плитку **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="9c435-159">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="9c435-160">На новой вкладке **SharePoint** в браузере выберите сайт, которому нужно назначить метку Office 365.</span><span class="sxs-lookup"><span data-stu-id="9c435-160">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="9c435-161">На новой вкладке SharePoint в браузере щелкните **Документы**.</span><span class="sxs-lookup"><span data-stu-id="9c435-161">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="9c435-162">Щелкните значок параметров, а затем **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="9c435-162">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="9c435-163">В разделе **Разрешения и управление** нажмите **Применить метку к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="9c435-163">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="9c435-164">В разделе **Параметры — применение метки** выберите соответствующую метку, а затем нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="9c435-164">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="9c435-165">Закройте вкладку сайта SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c435-165">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="9c435-166">Повторите шаги с 3 по 8, чтобы назначить метки Office 365 для дополнительных сайтов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c435-166">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="9c435-167">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="9c435-167">Here is your resulting configuration.</span></span>
  
![Метки Office 365 для четырех типов сайтов групп SharePoint Online.](media/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="9c435-169">Политики защиты от потери данных для сайтов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c435-169">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="9c435-170">Выполните следующие действия, чтобы настроить политику защиты от потери данных, которая уведомляет пользователей, когда они совместно используют документы на конфиденциальном сайте группы SharePoint Online за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="9c435-170">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="9c435-171">На вкладке браузера **Домашняя страница Microsoft Office** щелкните плитку **Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="9c435-171">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="9c435-172">На новой вкладке **Безопасность и соответствие требованиям** выберите **Защита от потери данных > Политика**.</span><span class="sxs-lookup"><span data-stu-id="9c435-172">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="9c435-173">В области **Защита от потери данных** нажмите кнопку **+ Создание политики**.</span><span class="sxs-lookup"><span data-stu-id="9c435-173">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="9c435-174">В области **Начните с шаблона или создайте настраиваемую политику** выберите **Настраиваемая**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-174">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="9c435-175">В области **Укажите имя для политики** введите название для политики защиты от потери конфиденциальных данных в поле **Имя**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-175">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="9c435-176">В области **Выбор расположений** щелкните **Let me choose specific locations** (Предоставить мне выбор конкретных расположений) и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-176">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="9c435-177">В списке расположений отключите параметры **Электронная почта Exchange** и **Учетные записи OneDrive**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-177">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="9c435-178">В области **Выберите тип содержимого, которое вы хотите защитить** щелкните ссылку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="9c435-178">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="9c435-179">В области **Выбрать типы содержимого для защиты** выберите **Добавить** в раскрывающемся списке, а затем выберите **Метки**.</span><span class="sxs-lookup"><span data-stu-id="9c435-179">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="9c435-180">В области **Метки** нажмите кнопку **+ Добавить**, укажите метку **Конфиденциальный** и последовательно нажмите кнопки **Добавить** > **Готово**.</span><span class="sxs-lookup"><span data-stu-id="9c435-180">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="9c435-181">В области **Выбрать типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="9c435-181">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="9c435-182">В области **Customize the types of sensitive info you want to protect** (Настройка типов защищаемых конфиденциальных сведений) нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-182">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="9c435-183">В области **What do you want to do if we detect sensitive info?** (Что делать при обнаружении конфиденциальной информации?) щелкните **Customize the tip and email** (Настроить подсказки и уведомления по электронной почте).</span><span class="sxs-lookup"><span data-stu-id="9c435-183">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="9c435-184">В области **Customize policy tips and email notifications** (Настройка подсказок политики и уведомления по электронной почте) щелкните **Customize the policy tip text** (Настроить текст подсказки политики).</span><span class="sxs-lookup"><span data-stu-id="9c435-184">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="9c435-185">В текстовом поле введите или вставьте одну из следующих подсказок в зависимости от того, применена ли служба Azure Information Protection, чтобы защитить строго конфиденциальные файлы:</span><span class="sxs-lookup"><span data-stu-id="9c435-185">In the text box, type or paste in one of the following tips, depending on if you implemented Azure Information Protection to protect highly confidential files:</span></span>
    
  - <span data-ttu-id="9c435-p106">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="9c435-p106">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
  - <span data-ttu-id="9c435-p107">Строго конфиденциальные файлы защищены с помощью шифрования. Их могут просматривать только те внешние пользователи, которым ваш ИТ-отдел предоставил разрешения для этих файлов.</span><span class="sxs-lookup"><span data-stu-id="9c435-p107">Highly confidential files are protected with encryption. Only external users who are granted permissions to these files by your IT department can read them.</span></span>
    
    <span data-ttu-id="9c435-p108">Вы также можете ввести или вставить, скопировав, собственную подсказку политики, которая укажет пользователям, как делиться файлом с людьми за пределами организации. Дополнительные сведения по предоставлению разрешений внешним пользователям для файлов, защищенных с помощью службы Azure Information Protection см. в статье "Добавление разрешений для внешних пользователей".</span><span class="sxs-lookup"><span data-stu-id="9c435-p108">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization. For more information on giving external users permissions to files protected wiht Azure Information Protection, see Adding permissions for external users.</span></span>
    
16. <span data-ttu-id="9c435-193">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="9c435-193">Click **OK**.</span></span>
    
17. <span data-ttu-id="9c435-194">В области **Что делать при обнаружении конфиденциальной информации?** снимите флажки **Запретить пользователям делиться контентом и ограничить доступ к совместно используемому содержимому**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-194">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="9c435-195">В области **Включить политику или сначала протестировать ее?** выберите пункт **Да, включить ее сразу**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-195">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="9c435-196">В области **Проверка параметров** нажмите **Создать**, а затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="9c435-196">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="9c435-197">Здесь показана итоговая конфигурация для конфиденциальных сайтов групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c435-197">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![Политика защиты от потери данных для изолированного сайта группы SharePoint Online с использованием метки "Конфиденциальный" в Office 365.](media/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="9c435-199">Выполните следующие действия, чтобы настроить политику защиты от потери данных, которая блокирует пользователей, когда они совместно используют документы на строго конфиденциальном сайте группы SharePoint Online за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="9c435-199">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="9c435-200">На вкладке браузера **Домашняя страница Microsoft Office** щелкните плитку **Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="9c435-200">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="9c435-201">На новой вкладке **Безопасность и соответствие требованиям** выберите **Защита от потери данных > Политика**.</span><span class="sxs-lookup"><span data-stu-id="9c435-201">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="9c435-202">В области **Защита от потери данных** нажмите кнопку **+ Создание политики**.</span><span class="sxs-lookup"><span data-stu-id="9c435-202">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="9c435-203">В области **Начните с шаблона или создайте настраиваемую политику** выберите **Настраиваемая**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-203">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="9c435-204">В области **Укажите имя для политики** введите название для политики защиты от потери строго конфиденциальных данных в поле **Имя**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-204">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="9c435-205">В области **Выбор расположений** щелкните **Let me choose specific locations** (Предоставить мне выбор конкретных расположений) и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-205">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="9c435-206">В списке расположений отключите параметры **Электронная почта Exchange** и **Учетные записи OneDrive**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-206">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="9c435-207">В области **Выберите тип содержимого, которое вы хотите защитить** щелкните ссылку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="9c435-207">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="9c435-208">В области **Выбрать типы содержимого для защиты** выберите **Добавить** в раскрывающемся списке, а затем выберите **Метки**.</span><span class="sxs-lookup"><span data-stu-id="9c435-208">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="9c435-209">В области **Метки** нажмите кнопку **+ Добавить**, выберите метку **Строго конфиденциальный**, нажмите **Добавить**, а затем нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="9c435-209">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="9c435-210">В области **Выбрать типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="9c435-210">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="9c435-211">В области **Customize the types of sensitive info you want to protect** (Настройка типов защищаемых конфиденциальных сведений) нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-211">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="9c435-212">В области **What do you want to do if we detect sensitive info?** (Что делать при обнаружении конфиденциальной информации?) щелкните **Customize the tip and email** (Настроить подсказки и уведомления по электронной почте).</span><span class="sxs-lookup"><span data-stu-id="9c435-212">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="9c435-213">В области **Customize policy tips and email notifications** (Настройка подсказок политики и уведомления по электронной почте) щелкните **Customize the policy tip text** (Настроить текст подсказки политики).</span><span class="sxs-lookup"><span data-stu-id="9c435-213">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="9c435-214">В текстовом поле введите или вставьте следующее:</span><span class="sxs-lookup"><span data-stu-id="9c435-214">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="9c435-p109">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Выберите пункты "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="9c435-p109">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="9c435-218">Вы также можете ввести или вставить, скопировав, собственную подсказку политики, которая укажет пользователям, как делиться файлом с людьми за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="9c435-218">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="9c435-219">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="9c435-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="9c435-220">В области **Что делать при обнаружении конфиденциальной информации?** выберите **Требовать коммерческое обоснование для переопределения**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-220">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="9c435-221">В области **Включить политику или сначала протестировать ее?** выберите пункт **Да, включить ее сразу**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="9c435-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="9c435-222">В области **Проверка параметров** нажмите **Создать**, а затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="9c435-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="9c435-223">Ниже показана итоговая конфигурация для строго конфиденциальных сайтов групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c435-223">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![Политика защиты от потери данных для изолированного сайта группы SharePoint Online с использованием метки "Строго конфиденциальный" в Office 365.](media/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="9c435-225">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="9c435-225">Next step</span></span>

[<span data-ttu-id="9c435-226">Защита файлов SharePoint Online с помощью Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="9c435-226">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="9c435-227">См. также</span><span class="sxs-lookup"><span data-stu-id="9c435-227">See Also</span></span>

[<span data-ttu-id="9c435-228">Безопасность сайтов и файлов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c435-228">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="9c435-229">Защита сайтов SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="9c435-229">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="9c435-230">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="9c435-230">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="9c435-231">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="9c435-231">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


