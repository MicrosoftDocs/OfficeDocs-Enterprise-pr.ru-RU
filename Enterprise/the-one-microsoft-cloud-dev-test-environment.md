---
title: "Среда разработки и тестирования One Microsoft Cloud"
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
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: "Сводка: Используйте руководство в лаборатории тестирования для создания среды разработки или тестирования, которая включает в себя все облака корпорации Майкрософт."
ms.openlocfilehash: 2cbfb3e963927f18d2ee46ed1f5076b274a99154
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="86861-103">Среда разработки и тестирования One Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="86861-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="86861-104">**Сводка:** В этом документе Test Lab Guide используйте для создания среды разработки или тестирования, которая включает в себя все облака корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="86861-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="86861-p101">Инструкции из этой статьи помогут создать имитируемую интрасеть в службах инфраструктуры Microsoft Azure, а затем добавить подписки на Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) и Microsoft Dynamics 365. В результате вы получите упрощенную организацию, которая использует все облачные решения Майкрософт одновременно в одной среде тестирования и разработки. </span><span class="sxs-lookup"><span data-stu-id="86861-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Этап 3 для среды разработки и тестирования One Microsoft Cloud с Azure, Office 365, EMS и Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="86861-108">Полученную в итоге конфигурацию можно использовать, чтобы:</span><span class="sxs-lookup"><span data-stu-id="86861-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="86861-109">опробовать интеграцию облачных решений Майкрософт, таких как общая инфраструктура идентификации, которую обеспечивает Azure Active Directory (AD);</span><span class="sxs-lookup"><span data-stu-id="86861-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="86861-110">оценить комплексные сценарии, включающие несколько решений Microsoft Cloud;</span><span class="sxs-lookup"><span data-stu-id="86861-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="86861-111">создать демоверсию конфигурации, конфигурацию для подтверждения концепции или конфигурацию для тестирования и разработки, которая использует несколько решений Microsoft Cloud;</span><span class="sxs-lookup"><span data-stu-id="86861-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="86861-112">развить свои навыки работы с Microsoft Cloud для профессионального роста.</span><span class="sxs-lookup"><span data-stu-id="86861-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="86861-113">Этап 1. Создание имитированной интрасети и добавление Office 365</span><span class="sxs-lookup"><span data-stu-id="86861-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="86861-114">Следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="86861-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="86861-115">На рисунке 1 показано итоговый конфигурации, включая Office 365 и имитации интрасети под управлением служб инфраструктуры и синхронизации каталогов в из локального леса Active Directory Windows Server (AD).</span><span class="sxs-lookup"><span data-stu-id="86861-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="86861-116">**На рисунке 1: Имитации интрасети в Azure с Office 365**</span><span class="sxs-lookup"><span data-stu-id="86861-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![Среда разработки и тестирования Office 365 с DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="86861-p102">Azure пробной версии — 30 дней. Пробная версия Enterprise E5 Office 365 подписки — 30 дней, которые могут быть легко расширены еще 30 дней. Для постоянного dev/тестовой среды создайте новую оплата за подпиской Azure и новой платной подписки Office 365 корпоративный E5 с небольшого числа лицензий.</span><span class="sxs-lookup"><span data-stu-id="86861-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="86861-121">Этап 2. Добавление EMS</span><span class="sxs-lookup"><span data-stu-id="86861-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="86861-122">На этом этапе можно оформить пробную подписку на EMS и добавить ее к той же организации, что и пробную подписку на Office 365.</span><span class="sxs-lookup"><span data-stu-id="86861-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="86861-123">С помощью браузера на одном компьютере или из CLIENT1, войдите в портал Office 365 на [https://portal.office.com](https://portal.office.com) с использованием учетных данных учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="86861-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="86861-124">Щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="86861-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="86861-125">На вкладке **центра администрирования Office** в браузере на панели навигации слева щелкните **выставления счетов > службы приобретения**.</span><span class="sxs-lookup"><span data-stu-id="86861-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="86861-p103">На странице " **службы приобретения** " Поиск элемента **мобильной работы предприятия + E5 безопасности** . Наведите указатель мыши на его и нажмите кнопку **Пуск бесплатную пробную версию**.</span><span class="sxs-lookup"><span data-stu-id="86861-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="86861-128">На странице " **Подтверждение заказа** " щелкните **Теперь попробуйте**.</span><span class="sxs-lookup"><span data-stu-id="86861-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="86861-129">На странице **получения заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="86861-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="86861-p104">Период пробной подписки на Enterprise Mobility + Security E5 составляет 90 дней. Чтобы создать постоянную среду тестирования и разработки, создайте новую платную подписку с небольшим количеством лицензий.</span><span class="sxs-lookup"><span data-stu-id="86861-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="86861-132">Далее включите лицензию на Enterprise Mobility + Security E5 для всех учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="86861-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="86861-133">На вкладке **Центр администрирования Office 365** в браузере на панели навигации слева щелкните **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="86861-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="86861-134">Выберите учетную запись глобального администратора и нажмите кнопку **Изменить** для **лицензий на продукт**.</span><span class="sxs-lookup"><span data-stu-id="86861-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="86861-135">В области **лицензий на продукт** включить лицензии для **мобильных устройств предприятия + E5 безопасности** для **на**, нажмите кнопку **Сохранить** и дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="86861-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="86861-136">Для всех других учетных записей (User1, User 2, User 3, User 4 и User 5) выполните действия 2 и 3.</span><span class="sxs-lookup"><span data-stu-id="86861-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="86861-137">Теперь ваша среда разработки и тестирования содержит следующее:</span><span class="sxs-lookup"><span data-stu-id="86861-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="86861-138">имитированную интрасеть в службах инфраструктуры Azure;</span><span class="sxs-lookup"><span data-stu-id="86861-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="86861-139">пробные подписки на Office 365 корпоративный E5 и EMS для одной организации, а также один и тот же клиент Azure AD для всех учетных записей пользователей из списка;</span><span class="sxs-lookup"><span data-stu-id="86861-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="86861-140">все учетные записи пользователей могут использовать Office 365 корпоративный E5 и EMS.</span><span class="sxs-lookup"><span data-stu-id="86861-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="86861-141">На рисунке 2 показана полученная в итоге конфигурация с EMS.</span><span class="sxs-lookup"><span data-stu-id="86861-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="86861-142">**На рисунке 2: Имитации интрасети в Azure с Office 365 и Командной**</span><span class="sxs-lookup"><span data-stu-id="86861-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Этап 2 для среды разработки и тестирования One Microsoft Cloud с Azure, Office 365 и EMS](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="86861-144">Этап 3: Добавление Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="86861-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="86861-145">На этом этапе можно оформить пробную подписку на Dynamics 365 и добавить ее к той же организации, что и пробные подписки на Office 365 и EMS.</span><span class="sxs-lookup"><span data-stu-id="86861-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="86861-146">С помощью браузера на одном компьютере или из CLIENT1, войдите в портал Office 365 на [https://portal.office.com](https://portal.office.com) с использованием учетных данных учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="86861-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="86861-147">Щелкните плитку **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="86861-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="86861-148">На вкладке **Центр администрирования Office** на панели навигации слева щелкните **выставления счетов > службы приобретения**.</span><span class="sxs-lookup"><span data-stu-id="86861-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="86861-p105">На странице " **службы приобретения** " Поиск элемента **Dynamics 365 планирование 1 Enterprise Edition** . Наведите указатель мыши на его и нажмите кнопку **Пуск бесплатную пробную версию**.</span><span class="sxs-lookup"><span data-stu-id="86861-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="86861-151">На странице " **Подтверждение заказа** " щелкните **Теперь попробуйте**.</span><span class="sxs-lookup"><span data-stu-id="86861-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="86861-152">На странице **получения заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="86861-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="86861-p106">Пробная подписка на Dynamics 365 Plan 1 Enterprise Edition действует 30 дней. Вы легко можете продлить ее еще на 30 дней. Чтобы создать постоянную среду тестирования и разработки, создайте новую платную подписку с небольшим количеством лицензий.</span><span class="sxs-lookup"><span data-stu-id="86861-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="86861-156">Эти инструкции помогут назначить лицензии на Dynamics 365 глобальному администратору, учетным записям User 2 и User 3 и сделать их системными администраторами.</span><span class="sxs-lookup"><span data-stu-id="86861-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="86861-157">На вкладке **Центр администрирования Office** щелкните **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="86861-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="86861-158">В список активных пользователей щелкните учетную запись глобального администратора и нажмите кнопку **Изменить** для **лицензий на продукт**.</span><span class="sxs-lookup"><span data-stu-id="86861-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="86861-159">В области **лицензий на продукт** включить лицензии для **Dynamics 365 планирование 1 Enterprise Edition** **на**, нажмите кнопку **Сохранить** и дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="86861-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="86861-160">Повторите шаги 2 и 3 для учетных записей пользователей User 2 и User 3.</span><span class="sxs-lookup"><span data-stu-id="86861-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="86861-161">Закройте вкладку **Центр администрирования Office** .</span><span class="sxs-lookup"><span data-stu-id="86861-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="86861-162">Выполните следующие действия, чтобы сделать учетные записи User 2 и User 3 системными администраторами Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="86861-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="86861-163">На вкладке **центра администрирования Office** в браузере на панели навигации слева щелкните **центры администрирования**и нажмите кнопку **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="86861-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="86861-164">Возможно, вам придется подождать окончания подготовки системы, прежде чем в меню появится пункт Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="86861-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="86861-165">На вкладке Dynamics 365 щелкните **все эти**и нажмите кнопку **завершить настройку.**</span><span class="sxs-lookup"><span data-stu-id="86861-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="86861-166">Подождите окончания операции.</span><span class="sxs-lookup"><span data-stu-id="86861-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="86861-p107">После завершения установки отображается на основе образца данных, который является частью подписки журнала активности панели мониторинга продаж. Занять некоторое время для просмотра **Добро пожаловать пробную версию** видео. Закройте окно видео после завершения.</span><span class="sxs-lookup"><span data-stu-id="86861-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="86861-170">На панели инструментов вверху щелкните стрелку вниз рядом с пунктом **Sales**, нажмите кнопку **Параметры**и нажмите кнопку **Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="86861-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="86861-171">На странице " **Безопасность** " щелкните **Пользователи**.</span><span class="sxs-lookup"><span data-stu-id="86861-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="86861-172">В списке пользователей выберите **пользователей 2**.</span><span class="sxs-lookup"><span data-stu-id="86861-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="86861-173">В панели инструментов нажмите кнопку **Управление ролями**.</span><span class="sxs-lookup"><span data-stu-id="86861-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="86861-174">**Управление ролями**щелкните **Системный администратор**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="86861-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="86861-175">В панели инструментов вверху щелкните **Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="86861-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="86861-176">Повторите действия 5–8 для учетной записи User 3.</span><span class="sxs-lookup"><span data-stu-id="86861-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="86861-177">Закрытие **пользователя: User3** вкладки.</span><span class="sxs-lookup"><span data-stu-id="86861-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="86861-178">Вашей учетной записи глобального администратора Office 365 автоматически назначена роль системного администратора Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="86861-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="86861-179">Теперь ваша среда разработки и тестирования содержит следующее:</span><span class="sxs-lookup"><span data-stu-id="86861-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="86861-180">имитированную интрасеть в службах инфраструктуры Azure;</span><span class="sxs-lookup"><span data-stu-id="86861-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="86861-181">пробные подписки на Office 365 корпоративный E5, EMS и Dynamics 365 для одной организации, а также один и тот же клиент Azure AD для всех учетных записей пользователей из списка;</span><span class="sxs-lookup"><span data-stu-id="86861-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="86861-182">все учетные записи пользователей могут использовать Office 365 корпоративный E5 и EMS;</span><span class="sxs-lookup"><span data-stu-id="86861-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="86861-183">учетным записям глобального администратора и пользователей User 2 и User 3 предоставлено разрешение использовать Dynamics 365 и назначена роль системного администратора Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="86861-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="86861-184">На рисунке 3 показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="86861-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="86861-185">**На рисунке 3: Имитации интрасети в Azure с Office 365, Командной и Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="86861-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Этап 3 для среды разработки и тестирования One Microsoft Cloud с Azure, Office 365, EMS и Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="86861-187">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="86861-187">Next steps</span></span>

<span data-ttu-id="86861-p108">Теперь вы можете экспериментировать в среде тестирования и разработки One Microsoft Cloud. Вот несколько статей, если вам при этом понадобятся рекомендации:</span><span class="sxs-lookup"><span data-stu-id="86861-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="86861-190">Настройка политик управления (MAM) мобильных приложений в Командной для приложений Office 365</span><span class="sxs-lookup"><span data-stu-id="86861-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="86861-191">Демонстрация Exchange Online в Office 365 интеграции с контактами Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="86861-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="86861-192">Создание имитации распределенной сети в службах инфраструктуры для размещения рабочих нагрузок на стороне сервера</span><span class="sxs-lookup"><span data-stu-id="86861-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="86861-193">См. также</span><span class="sxs-lookup"><span data-stu-id="86861-193">See Also</span></span>

[<span data-ttu-id="86861-194">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="86861-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="86861-195">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="86861-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="86861-196">Гибридные решения</span><span class="sxs-lookup"><span data-stu-id="86861-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="86861-197">Решения для обеспечения безопасности</span><span class="sxs-lookup"><span data-stu-id="86861-197">Security solutions</span></span>](security-solutions.md)





