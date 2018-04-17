---
title: Среда разработки и тестирования для Office 365 и Dynamics 365
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
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Сводка: Используйте руководство в лаборатории тестирования для добавления Dynamics 365 dev/тестовой среде Office 365.'
ms.openlocfilehash: 24f121c9e5f8a25bae61ce4a59b42d528ffbda17
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="c3406-103">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c3406-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="c3406-104">**Сводка:** Используйте в этом документе Test Lab Guide для добавления Dynamics 365 dev/тестовой среде Office 365.</span><span class="sxs-lookup"><span data-stu-id="c3406-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="c3406-105">Следуя инструкциям в этой статье, вы добавите пробную подписку на Dynamics 365 к той же организации, к которой относится среда разработки и тестирования Office 365, и создадите среду разработки и тестирования Office 365 и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c3406-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
<span data-ttu-id="c3406-p101">Используйте пробную подписку на Dynamics 365 для демонстрации функций и возможностей системы. Пробная подписка Dynamics 365 Plan 1, Enterprise Edition включает следующие решения:</span><span class="sxs-lookup"><span data-stu-id="c3406-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="c3406-p102">[Microsoft Dynamics 365 продаж](https://www.microsoft.com/dynamics365/sales). Увеличьте объем продаж с помощью автоматизации и цифровых аналитики, как помочь менеджеров сосредоточено и организации работы.</span><span class="sxs-lookup"><span data-stu-id="c3406-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="c3406-p103">[Microsoft Dynamics 365 для обслуживания клиентов](https://www.microsoft.com/dynamics365/customer-service). Получите постоянных клиентов, предоставляя ее агентов полные сведения и цифровых необходимы для обеспечения эффективной службы аналитики.</span><span class="sxs-lookup"><span data-stu-id="c3406-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="c3406-p104">[Microsoft Dynamics 365 для службы поля](https://www.microsoft.com/dynamics365/field-service). Хозяин вызова службы, оптимизация расписания, снабдив рабочей силы и с помощью средства упреждающий увеличение прибыли.</span><span class="sxs-lookup"><span data-stu-id="c3406-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="c3406-p105">[Microsoft Dynamics 365 для автоматизации службы Project](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Успешного завершения проектов и создайте выгодных отношений с производительности сотрудников и интеллектуальные средства.</span><span class="sxs-lookup"><span data-stu-id="c3406-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="c3406-116">С пробной подпиской на Dynamics 365 вы можете опробовать любое из перечисленных выше решений или ознакомиться с другими вариантами.</span><span class="sxs-lookup"><span data-stu-id="c3406-116">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Руководства по лаборатории тестирования в Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="c3406-118">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="c3406-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="c3406-119">Этап 1. Создание среды разработки и тестирования Office 365 — упрощенной или для имитированных предприятий</span><span class="sxs-lookup"><span data-stu-id="c3406-119">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="c3406-120">Если необходимо проверить Dynamics 365 и Office 365 в облегченный путь с минимальным требованиям, следуйте инструкциям в этапы 2 и 3 [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c3406-120">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c3406-121">Если вы хотите проверить Dynamics 365 и Office 365 для имитации enterprise, следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c3406-121">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c3406-p106">Для конфигурации, описанной в данной статье, не требуется среда разработки и тестирования имитированного предприятия, которая включает имитацию интрасети с подключением к Интернету и синхронизацию каталогов леса Windows Server AD. Эти возможности представлены здесь лишь для того, чтобы вы могли поэкспериментировать с Office 365 и Dynamics 365 в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="c3406-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="c3406-124">Этап 2. Добавление пробной подписки на Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c3406-124">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="c3406-125">На этом этапе можно оформить пробную подписку на Dynamics 365 и добавить ее к той же организации, что и пробную подписку на Office 365.</span><span class="sxs-lookup"><span data-stu-id="c3406-125">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="c3406-126">Оформление пробной подписки на Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c3406-126">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="c3406-127">С помощью браузера на любой компьютер (lightweight) или от CLIENT1 (моделируемые enterprise), вход на портал Office 365 по [https://portal.office.com](https://portal.office.com) с использованием учетных данных учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c3406-127">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="c3406-128">Выберите плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="c3406-128">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c3406-129">На вкладке **Центр администрирования Office** на панели навигации слева щелкните **выставления счетов > службы приобретения**.</span><span class="sxs-lookup"><span data-stu-id="c3406-129">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="c3406-p107">На странице " **службы приобретения** " Поиск элемента **Dynamics 365 планирование 1 Enterprise Edition** . Наведите указатель мыши на его и нажмите кнопку **Пуск бесплатную пробную версию**.</span><span class="sxs-lookup"><span data-stu-id="c3406-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="c3406-132">На странице **Подтверждение заказа** щелкните **Попробовать сейчас**.</span><span class="sxs-lookup"><span data-stu-id="c3406-132">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="c3406-133">На странице **Получение заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="c3406-133">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c3406-p108">Пробная подписка на Dynamics 365 Plan 1 Enterprise Edition действует 30 дней. Вы легко можете продлить ее еще на 30 дней. Чтобы создать постоянную среду тестирования и разработки, создайте новую платную подписку с небольшим количеством лицензий.</span><span class="sxs-lookup"><span data-stu-id="c3406-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="c3406-137">Этап 3. Назначение лицензий и системных администраторов Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c3406-137">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="c3406-138">На этом этапе необходимо назначить лицензии Dynamics 365 глобальному администратору, учетным записям User 2 и User 3 и сделать их системными администраторами.</span><span class="sxs-lookup"><span data-stu-id="c3406-138">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="c3406-139">Выполните следующие действия, чтобы назначить лицензии Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c3406-139">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="c3406-140">На вкладке **Центр администрирования Office** щелкните **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="c3406-140">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="c3406-141">В список активных пользователей щелкните учетную запись глобального администратора и нажмите кнопку **Изменить** для **лицензий на продукт**.</span><span class="sxs-lookup"><span data-stu-id="c3406-141">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="c3406-142">В области **лицензий на продукт** включить лицензии для **Dynamics 365 планирование 1 Enterprise Edition** **на**, нажмите кнопку **Сохранить** и дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="c3406-142">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="c3406-143">Повторите шаги 2 и 3 для учетных записей пользователей User 2 и User 3.</span><span class="sxs-lookup"><span data-stu-id="c3406-143">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="c3406-144">Закройте вкладку **Центр администрирования Office** .</span><span class="sxs-lookup"><span data-stu-id="c3406-144">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="c3406-145">Выполните следующие действия, чтобы сделать учетные записи User 2 и User 3 системными администраторами Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c3406-145">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="c3406-146">Откройте вкладку **Microsoft Office для дома** и щелкните **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="c3406-146">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="c3406-147">На вкладке **центра администрирования Office** на панели навигации слева щелкните **центры администрирования**и нажмите кнопку **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="c3406-147">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="c3406-148">Возможно, вам придется подождать окончания подготовки системы, прежде чем в меню появится пункт Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c3406-148">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="c3406-149">На вкладке Dynamics 365 щелкните **все эти**и нажмите кнопку **завершить настройку.**</span><span class="sxs-lookup"><span data-stu-id="c3406-149">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="c3406-150">Подождите окончания операции.</span><span class="sxs-lookup"><span data-stu-id="c3406-150">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="c3406-p109">После завершения установки отображается на основе образца данных, который является частью подписки журнала активности панели мониторинга продаж. Занять некоторое время для просмотра **Добро пожаловать пробную версию** видео. Закройте окно видео после завершения.</span><span class="sxs-lookup"><span data-stu-id="c3406-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="c3406-154">На панели инструментов вверху щелкните стрелку вниз рядом с пунктом **Sales**, нажмите кнопку **Параметры**и нажмите кнопку **Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="c3406-154">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="c3406-155">На странице " **Безопасность** " щелкните **Пользователи**.</span><span class="sxs-lookup"><span data-stu-id="c3406-155">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="c3406-156">В списке пользователей выберите **пользователей 2**.</span><span class="sxs-lookup"><span data-stu-id="c3406-156">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="c3406-157">В панели инструментов нажмите кнопку **Управление ролями**.</span><span class="sxs-lookup"><span data-stu-id="c3406-157">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="c3406-158">**Управление ролями**щелкните **Системный администратор**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="c3406-158">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="c3406-159">В панели инструментов вверху щелкните **Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="c3406-159">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="c3406-160">Повторите действия 5–8 для учетной записи User 3.</span><span class="sxs-lookup"><span data-stu-id="c3406-160">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="c3406-161">Закрытие **пользователя: User3** вкладки.</span><span class="sxs-lookup"><span data-stu-id="c3406-161">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c3406-162">Вашей учетной записи глобального администратора Office 365 автоматически назначена роль системного администратора Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c3406-162">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="c3406-163">Теперь среда разработки и тестирования Office 365 и Dynamics 365 имеет следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="c3406-163">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="c3406-164">пробные подписки на Office 365 корпоративный E5 и Dynamics 365 для одной организации, а также один и тот же клиент Azure AD для всех учетных записей пользователей из списка;</span><span class="sxs-lookup"><span data-stu-id="c3406-164">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="c3406-165">в учетных записях глобального администратора и пользователей User 2 и User 3 включено право пользования Office 365 E5 Enterprise и Dynamics 365. Кроме того, всем им назначена роль системного администратора Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c3406-165">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="c3406-166">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="c3406-166">Next step</span></span>

<span data-ttu-id="c3406-167">Настройка и затем Демонстрация Office 365 Dynamics 365 совместная работа и почтовых ящиков в Exchange Online с помощью [интеграции с Exchange Online для Office 365 и Dynamics 365 dev/тестовой среды](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="c3406-167">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3406-168">См. также</span><span class="sxs-lookup"><span data-stu-id="c3406-168">See Also</span></span>

[<span data-ttu-id="c3406-169">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="c3406-169">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c3406-170">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="c3406-170">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="c3406-171">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="c3406-171">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="c3406-172">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="c3406-172">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="c3406-173">Управление подпиской для Dynamics 365 (сетевая версия)</span><span class="sxs-lookup"><span data-stu-id="c3406-173">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="c3406-174">Администрирование Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c3406-174">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


