---
title: "Защита файлов SharePoint Online с помощью Office 365 метки и защиты от потери данных"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: "Сводка: Применение Office 365 метки и данных политик предотвращения потери (DLP) для SharePoint Online сайтов группы с помощью различных уровней защиты информации."
ms.openlocfilehash: dd4f71d8fae458d6d20f7a5b35b46e14a72853f1
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="6def8-103">Защита файлов SharePoint Online с помощью Office 365 метки и защиты от потери данных</span><span class="sxs-lookup"><span data-stu-id="6def8-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="6def8-104">**Сводка:** Применение Office 365 метки и данных политик предотвращения потери (DLP) для SharePoint Online сайтов группы с помощью различных уровней защиты информации.</span><span class="sxs-lookup"><span data-stu-id="6def8-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="6def8-p101">Использование действия, описанные в этой статье для создания и развертывания Office 365 меток и политики защиты от потери данных для базового, конфиденциальных и конфиденциальными сайтов SharePoint Online группы. Дополнительные сведения об этих трех уровней защиты можно [безопасного SharePoint Online сайтами и файлами](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="6def8-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="6def8-107">Метки Office 365 для сайтов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6def8-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="6def8-108">Существует три этапа создания и назначения меток Office 365 для сайтов группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6def8-108">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="6def8-109">Этап 1. Определение имен меток Office 365</span><span class="sxs-lookup"><span data-stu-id="6def8-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="6def8-p102">На этом этапе нужно определить названия меток Office 365 для четырех уровней защиты информации, применяемых к сайтам группы SharePoint Online. В приведенной ниже таблице перечислены рекомендуемые имена для каждого уровня.</span><span class="sxs-lookup"><span data-stu-id="6def8-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="6def8-112">**SharePoint Online уровень защиты сайта группы**</span><span class="sxs-lookup"><span data-stu-id="6def8-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="6def8-113">**Имя метки**</span><span class="sxs-lookup"><span data-stu-id="6def8-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6def8-114">Базовый общедоступный</span><span class="sxs-lookup"><span data-stu-id="6def8-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="6def8-115">Внутренний общедоступный</span><span class="sxs-lookup"><span data-stu-id="6def8-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="6def8-116">Базовый частный</span><span class="sxs-lookup"><span data-stu-id="6def8-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="6def8-117">Частный</span><span class="sxs-lookup"><span data-stu-id="6def8-117">Private</span></span>  <br/> |
|<span data-ttu-id="6def8-118">Конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="6def8-118">Sensitive</span></span>  <br/> |<span data-ttu-id="6def8-119">Конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="6def8-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="6def8-120">Строго конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="6def8-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="6def8-121">Строго конфиденциальный</span><span class="sxs-lookup"><span data-stu-id="6def8-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="6def8-122">Этап 2. Создание меток Office 365</span><span class="sxs-lookup"><span data-stu-id="6def8-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="6def8-123">На этом этапе нужно создать и опубликовать определенные метки для разных уровней защиты информации.</span><span class="sxs-lookup"><span data-stu-id="6def8-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="6def8-124">Создать метки можно с помощью Microsoft PowerShell или Центра администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="6def8-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="6def8-125">Создание меток Office 365 в Центре администрирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6def8-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="6def8-p103">Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6def8-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6def8-128">Откройте вкладку **Microsoft Office для дома** и щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="6def8-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="6def8-129">В новую вкладку **Центр администрирования Office** обозревателя, выберите **центры администрирования > Безопасность &amp; соответствия**.</span><span class="sxs-lookup"><span data-stu-id="6def8-129">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="6def8-130">От нового **Home — безопасности &amp; соответствия** вкладки браузера, нажмите кнопку **классификаций > меток**.</span><span class="sxs-lookup"><span data-stu-id="6def8-130">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="6def8-131">Из **Домашняя страница > меток** области, нажмите кнопку **создать метку**.</span><span class="sxs-lookup"><span data-stu-id="6def8-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="6def8-132">В области **имя метки** введите имя метки и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-132">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6def8-133">В области **Параметры метки** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="6def8-134">На панели **Проверьте параметры** нажмите кнопку **Создать в этом метки**и нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6def8-134">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="6def8-135">Повторите действия 5–8, чтобы создать дополнительные метки.</span><span class="sxs-lookup"><span data-stu-id="6def8-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="6def8-136">Создание меток Office 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="6def8-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="6def8-137">[Подключение к Office 365 безопасность &amp; центре соответствия требованиям, с помощью удаленной оболочки PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) и укажите учетные данные учетной записи, имеющей роли безопасности администратора или администратора компании.</span><span class="sxs-lookup"><span data-stu-id="6def8-137">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="6def8-138">Заполните список имен меток, а затем запустите эти команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6def8-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="6def8-139">Для публикации новых меток Office 365 выполните действия, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="6def8-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="6def8-140">Из **Домашняя страница > меток** области безопасности &amp; центре соответствия требованиям, нажмите кнопку **Опубликовать метки**.</span><span class="sxs-lookup"><span data-stu-id="6def8-140">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="6def8-141">В области **выбора меток для публикации** выберите **Выбор меток для публикации**.</span><span class="sxs-lookup"><span data-stu-id="6def8-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="6def8-142">В области **выберите метки** нажмите кнопку **Добавить** и выберите пункт все четыре метки.</span><span class="sxs-lookup"><span data-stu-id="6def8-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="6def8-143">Нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6def8-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="6def8-144">В области **выбора меток для публикации** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="6def8-145">В области **выбора расположения** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="6def8-146">В области **Имя политики** введите имя для вашего набора меток в поле **имя**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6def8-147">В области **Проверьте параметры** нажмите кнопку **Опубликовать меток**и нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6def8-147">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="6def8-148">Этап 3. Применение меток Office 365 к сайтам SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6def8-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="6def8-149">Инструкции по применению меток Office 365 к папкам документов, размещенным на сайтах группы SharePoint Online, приведены ниже.</span><span class="sxs-lookup"><span data-stu-id="6def8-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="6def8-150">На вкладке **Microsoft Office для дома** браузера щелкните плитку **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="6def8-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="6def8-151">На новой вкладке **SharePoint** в браузере щелкните сайта, которое должно метку Office 365 назначены.</span><span class="sxs-lookup"><span data-stu-id="6def8-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="6def8-152">В новую вкладку сайта SharePoint из браузера щелкните **документы**.</span><span class="sxs-lookup"><span data-stu-id="6def8-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="6def8-153">Щелкните значок параметры и нажмите кнопку **Параметры библиотеки**.</span><span class="sxs-lookup"><span data-stu-id="6def8-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="6def8-154">В разделе **разрешения и управление**щелкните **метки применить к элементам в этой библиотеке**.</span><span class="sxs-lookup"><span data-stu-id="6def8-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="6def8-155">**Применение параметров метки**выберите соответствующую метку и нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6def8-155">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="6def8-156">Закройте вкладку сайта SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6def8-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="6def8-157">Повторите действия 3–8, чтобы назначить метки Office 365 для дополнительных сайтов SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6def8-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="6def8-158">Ниже показана полученная в итоге конфигурация.</span><span class="sxs-lookup"><span data-stu-id="6def8-158">Here is your resulting configuration.</span></span>
  
![Метки Office 365 для четырех типов сайтов группы SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="6def8-160">Политики защиты от потери данных для сайтов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6def8-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="6def8-161">Выполните следующие действия, чтобы настроить политику защиты от потери данных, которое уведомляет пользователей, если они совместного использования документов на сайте SharePoint Online конфиденциальные группы за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="6def8-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="6def8-162">На вкладке **Microsoft Office для дома** в браузере выберите **безопасности &amp; соответствия** заголовков.</span><span class="sxs-lookup"><span data-stu-id="6def8-162">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="6def8-163">В новом **безопасности &amp; соответствия** в браузере, щелкните **защиту от потери данных > политики**.</span><span class="sxs-lookup"><span data-stu-id="6def8-163">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="6def8-164">На левой панели **защиту от потери данных** нажмите кнопку **+ Создать политику**.</span><span class="sxs-lookup"><span data-stu-id="6def8-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="6def8-165">В **Начать с шаблоном или создайте пользовательскую политику** области, выберите **настраиваемые**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="6def8-166">В области **Имя политики** введите имя для конфиденциальных уровень политики защиты от потери данных в поле **имя**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-166">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="6def8-167">На левой панели **Выберите расположение** нажмите кнопку **выбрать определенные расположения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6def8-168">В списке расположений отключить расположения **учетных записей OneDrive** и **электронной почты Exchange** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6def8-169">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="6def8-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="6def8-170">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Добавить** , в раскрывающемся списке и нажмите кнопку **метки**.</span><span class="sxs-lookup"><span data-stu-id="6def8-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="6def8-171">В области **метки** нажмите кнопку **+ Добавить**, выберите **конфиденциальных** метку, нажмите кнопку **Добавить**и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6def8-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="6def8-172">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6def8-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="6def8-173">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="6def8-174">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, нажмите кнопку **Настройка подсказки и адрес электронной почты**.</span><span class="sxs-lookup"><span data-stu-id="6def8-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="6def8-175">В области **Настройка подсказок политики и уведомления по электронной почте** нажмите кнопку **Настройка текст подсказки политики**.</span><span class="sxs-lookup"><span data-stu-id="6def8-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="6def8-176">В текстовом поле введите или вставьте в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="6def8-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="6def8-p104">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Нажмите "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="6def8-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="6def8-180">Вы также можете ввести или вставить, скопировав, собственную подсказку политики, которая укажет пользователям, как делиться файлом с людьми за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="6def8-180">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="6def8-181">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6def8-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="6def8-182">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, снимите флажок **Блокировать людей из общего доступа и ограничить доступ к общее содержимое** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="6def8-183">В **хотите ли вы включить действия политики или тестирования сначала?** области, нажмите кнопку **Да, включить немедленно**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6def8-184">В области **Проверьте параметры** нажмите кнопку **Создать**и затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6def8-184">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="6def8-185">Ниже показана полученная в итоге конфигурация для конфиденциальных сайтов группы SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6def8-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![Политика защиты от потери данных для изолированного сайта группы SharePoint Online с использованием метки "Конфиденциальный" в Office 365.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="6def8-187">Ниже приведены инструкции по настройке политики защиты от потери данных, которая блокирует предоставление пользователями доступа к документам, размещенным на строго конфиденциальном сайте группы SharePoint Online, людям за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="6def8-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="6def8-188">На вкладке **Microsoft Office для дома** в браузере выберите **безопасности &amp; соответствия** заголовков.</span><span class="sxs-lookup"><span data-stu-id="6def8-188">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="6def8-189">В новом **безопасности &amp; соответствия** в браузере, щелкните **защиту от потери данных > политики**.</span><span class="sxs-lookup"><span data-stu-id="6def8-189">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="6def8-190">На левой панели **защиту от потери данных** нажмите кнопку **+ Создать политику**.</span><span class="sxs-lookup"><span data-stu-id="6def8-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="6def8-191">В **Начать с шаблоном или создайте пользовательскую политику** области, выберите **настраиваемые**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="6def8-192">В области **Имя политики** введите имя для очень важными уровень политики защиты от потери данных в поле **имя**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="6def8-193">На левой панели **Выберите расположение** нажмите кнопку **выбрать определенные расположения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6def8-194">В списке расположений отключить расположения **учетных записей OneDrive** и **электронной почты Exchange** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6def8-195">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="6def8-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="6def8-196">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Добавить** , в раскрывающемся списке и нажмите кнопку **метки**.</span><span class="sxs-lookup"><span data-stu-id="6def8-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="6def8-197">На левой панели **метки** нажмите кнопку **+ Добавить**, выберите метку **Конфиденциальными** , нажмите кнопку **Добавить**и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6def8-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="6def8-198">На левой панели **выберите типы содержимого для защиты** нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="6def8-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="6def8-199">В области **Настройка типов конфиденциальные сведения, которые необходимо защитить** нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="6def8-200">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, нажмите кнопку **Настройка подсказки и адрес электронной почты**.</span><span class="sxs-lookup"><span data-stu-id="6def8-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="6def8-201">В области **Настройка подсказок политики и уведомления по электронной почте** нажмите кнопку **Настройка текст подсказки политики**.</span><span class="sxs-lookup"><span data-stu-id="6def8-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="6def8-202">В текстовом поле введите или вставьте в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="6def8-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="6def8-p105">Чтобы предоставить доступ пользователю за пределами организации, скачайте файл и откройте его. Нажмите "Файл > Защитить документ > Зашифровать паролем", а затем укажите надежный пароль. Отправьте пароль в отдельном сообщении или с помощью других средств связи.</span><span class="sxs-lookup"><span data-stu-id="6def8-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="6def8-206">Вы также можете ввести или вставить, скопировав, собственную подсказку политики, которая укажет пользователям, как делиться файлом с людьми за пределами организации.</span><span class="sxs-lookup"><span data-stu-id="6def8-206">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="6def8-207">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6def8-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="6def8-208">В **необходимые действия, если мы обнаруживать конфиденциальные сведения?** области, выберите **Требовать деловое обоснование для переопределения**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="6def8-209">В **хотите ли вы включить действия политики или тестирования сначала?** области, нажмите кнопку **Да, включить немедленно**и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="6def8-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6def8-210">В области **Проверьте параметры** нажмите кнопку **Создать**и затем нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6def8-210">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="6def8-211">Ниже показана конфигурация сайтов группы SharePoint Online, для которых настроен уровень строгой конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="6def8-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![Политика защиты от потери данных для изолированного сайта группы SharePoint Online с использованием метки "Строго конфиденциальный" в Office 365.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="6def8-213">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="6def8-213">Next step</span></span>

[<span data-ttu-id="6def8-214">Защита файлов SharePoint Online с помощью Azure защита информации</span><span class="sxs-lookup"><span data-stu-id="6def8-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="6def8-215">См. также</span><span class="sxs-lookup"><span data-stu-id="6def8-215">See Also</span></span>

[<span data-ttu-id="6def8-216">Безопасность сайтов и файлов SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6def8-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="6def8-217">Защита сайтов SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="6def8-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="6def8-218">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="6def8-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="6def8-219">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="6def8-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


