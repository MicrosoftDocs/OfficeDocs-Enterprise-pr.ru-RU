---
title: Среда разработки и тестирования для Office 365 и Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: Сводка. В этом руководстве объясняется, как добавить Dynamics 365 в среду разработки и тестирования Office 365.
ms.openlocfilehash: 9e4c98129c68ab5d2f0d9fc486ab62740c625af5
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574063"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="2b3bf-103">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="2b3bf-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="2b3bf-104">**Сводка.** В этом руководстве объясняется, как добавить Dynamics 365 в среду разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="2b3bf-105">Следуя инструкциям в этой статье, вы добавите пробную подписку на Dynamics 365 к той же организации, к которой относится среда разработки и тестирования Office 365, и создадите среду разработки и тестирования Office 365 и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Среда разработки и тестирования для Office 365 и Dynamics 365](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="2b3bf-p101">Используйте пробную подписку на Dynamics 365 для демонстрации функций и возможностей системы. Пробная подписка Dynamics 365 Plan 1, Enterprise Edition включает следующие решения:</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="2b3bf-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Увеличивайте объемы продаж благодаря автоматизации и использованию функций цифровой аналитики, что позволит вашим сотрудникам сосредоточиться на работе.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="2b3bf-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Приобретайте лояльных клиентов, предоставляя агентам полную информацию и возможности цифровой аналитики, без которых обеспечить безупречный уровень обслуживания просто невозможно.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="2b3bf-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Научитесь управлять заявками на обслуживание благодаря оптимизации планирования, обеспечению сотрудников качественным оборудованием и использованию инструментов прогнозирования и увеличьте свою прибыль.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="2b3bf-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/ru-RU/dynamics365/project-service-automation). Успешно завершайте проекты и выстраивайте взаимовыгодные взаимоотношения с клиентами благодаря продуктивной работе персонала и использованию интеллектуальных инструментов.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/ru-RU/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="2b3bf-117">С пробной подпиской на Dynamics 365 вы можете опробовать любое из перечисленных выше решений или ознакомиться с другими вариантами.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Руководства по лаборатории тестирования в Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="2b3bf-119">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="2b3bf-120">Этап 1. Создание среды разработки и тестирования Office 365 — упрощенной или для имитированных предприятий</span><span class="sxs-lookup"><span data-stu-id="2b3bf-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="2b3bf-121">Если вам нужно лишь упрощенное (с минимальными требованиями) тестирование Office 365 и Dynamics 365, следуйте инструкциям в статье [Среда разработки и тестирования Office 365](office-365-dev-test-environment.md) (этапы 2 и 3).</span><span class="sxs-lookup"><span data-stu-id="2b3bf-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="2b3bf-122">Если вы хотите протестировать Office 365 и Dynamics 365 в среде имитированного предприятия, следуйте указаниям в статье [DirSync для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2b3bf-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![Среда разработки и тестирования Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="2b3bf-p106">Для конфигурации, описанной в данной статье, не требуется среда разработки и тестирования имитированного предприятия, которая включает имитацию интрасети с подключением к Интернету и синхронизацию каталогов леса Windows Server AD. Эти возможности представлены здесь лишь для того, чтобы вы могли поэкспериментировать с Office 365 и Dynamics 365 в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="2b3bf-126">Этап 2. Добавление пробной подписки на Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="2b3bf-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="2b3bf-127">На этом этапе можно оформить пробную подписку на Dynamics 365 и добавить ее к той же организации, что и пробную подписку на Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="2b3bf-128">Оформление пробной подписки на Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="2b3bf-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="2b3bf-129">С помощью браузера на настольном компьютере (упрощенное тестирование) или CLIENT1 (имитированное предприятие) войдите в Центр администрирования Microsoft 365 по адресу [https://admin.microsoft.com](https://admin.microsoft.com), используя данные учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://admin.microsoft.com](https://admin.microsoft.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="2b3bf-130">Выберите плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="2b3bf-131">На вкладке **Центра администрирования Microsoft 365**, в области навигации слева, нажмите **Выставление счетов > Приобретение служб**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-131">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="2b3bf-p107">На странице **Приобретение служб** найдите элемент **Dynamics 365 (план 1), выпуск Enterprise**. Наведите на него указатель мыши и выберите **Начать бесплатный пробный период**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="2b3bf-134">На странице **Подтверждение заказа** нажмите кнопку **Попробовать**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="2b3bf-135">На странице **Получение заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-135">On the **Order receipt** page, click **Continue**.</span></span>

![Среда разработки и тестирования для Office 365 и Dynamics 365](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="2b3bf-p108">Пробная подписка на Dynamics 365 Plan 1 Enterprise Edition действует 30 дней. Вы легко можете продлить ее еще на 30 дней. Чтобы создать постоянную среду тестирования и разработки, создайте новую платную подписку с небольшим количеством лицензий.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="2b3bf-140">Этап 3. Назначение лицензий и системных администраторов Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="2b3bf-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="2b3bf-141">На этом этапе необходимо назначить лицензии Dynamics 365 глобальному администратору, учетным записям User 2 и User 3 и сделать их системными администраторами.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="2b3bf-142">Выполните следующие действия, чтобы назначить лицензии Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="2b3bf-143">На вкладке **Центра администрирования Microsoft 365** выберите **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-143">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="2b3bf-144">В списке активных пользователей выберите свою учетную запись глобального администратора и щелкните ссылку **Изменить** для параметра **Лицензии на продукты**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="2b3bf-145">	На панели *\*Лицензии на продукты** переведите переключатель *\*Dynamics 365 (план 1), выпуск Enterprise** в положение *\*Вкл.*\*, нажмите *\*Сохранить*\*, а затем дважды *\*Закрыть*\*.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="2b3bf-146">Повторите шаги 2 и 3 для учетных записей пользователей User 2 и User 3.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="2b3bf-147">Закройте вкладку **Центра администрирования Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-147">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="2b3bf-148">Выполните следующие действия, чтобы сделать учетные записи User 2 и User 3 системными администраторами Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="2b3bf-149">На главной вкладке **Microsoft Office** щелкните **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="2b3bf-150">На вкладке **Центр администрирования Office** в области навигации слева выберите пункт **Центры администрирования**, а затем выберите элемент **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="2b3bf-151">Возможно, вам придется подождать окончания подготовки системы, прежде чем в меню появится пункт Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="2b3bf-152">На вкладке "Dynamics 365" выберите **Все вышеперечисленное** и нажмите **Завершить установку**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="2b3bf-153">Подождите окончания операции.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="2b3bf-p109">После завершения установки появится панель управления продажами с демонстрационными данными, которые входят в пробную подписку. Просмотрите **ознакомительное видео**. Закройте окно с видео, когда закончите.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="2b3bf-157">На панели инструментов сверху нажмите стрелку вниз рядом с параметром **Продажи** и последовательно выберите **Параметры** > **Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="2b3bf-158">На странице **Безопасность** нажмите **Пользователи**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="2b3bf-159">В списке пользователей выберите **User 2**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="2b3bf-160">На панели инструментов выберите **Управление ролями**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="2b3bf-161">В окне **Управление ролями** установите флажок **Системный администратор** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="2b3bf-162">На панели инструментов сверху нажмите **Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="2b3bf-163">Повторите действия 5–8 для учетной записи User 3.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="2b3bf-164">Закройте вкладку **Пользователь: User3**.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="2b3bf-165">Вашей учетной записи глобального администратора Office 365 автоматически назначена роль системного администратора Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="2b3bf-166">Теперь среда разработки и тестирования Office 365 и Dynamics 365 имеет следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="2b3bf-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="2b3bf-167">пробные подписки на Office 365 корпоративный E5 и Dynamics 365 для одной организации, а также один и тот же клиент Azure AD для всех учетных записей пользователей из списка;</span><span class="sxs-lookup"><span data-stu-id="2b3bf-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="2b3bf-168">в учетных записях глобального администратора и пользователей User 2 и User 3 включено право пользования Office 365 E5 Enterprise и Dynamics 365. Кроме того, всем им назначена роль системного администратора Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="2b3bf-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="2b3bf-169">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="2b3bf-169">Next step</span></span>

<span data-ttu-id="2b3bf-170">Настройте и продемонстрируйте совместную работу Office 365 и Dynamics 365 в почтовых ящиках Exchange Online с использованием статьи [Интеграция с Exchange Online для среды разработки и тестирования Office 365 и Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="2b3bf-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2b3bf-171">См. также</span><span class="sxs-lookup"><span data-stu-id="2b3bf-171">See Also</span></span>

[<span data-ttu-id="2b3bf-172">Руководства по созданию сред разработки и тестирования облачных решений</span><span class="sxs-lookup"><span data-stu-id="2b3bf-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="2b3bf-173">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="2b3bf-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="2b3bf-174">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="2b3bf-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="2b3bf-175">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="2b3bf-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="2b3bf-176">Управление подпиской для Dynamics 365 (сетевая версия)</span><span class="sxs-lookup"><span data-stu-id="2b3bf-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="2b3bf-177">Администрирование Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="2b3bf-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


