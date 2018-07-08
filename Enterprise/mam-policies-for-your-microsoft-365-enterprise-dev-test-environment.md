---
title: Политики MAM для вашей среды разработки и тестирования Microsoft 365 корпоративный
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 'Сводка: Используйте руководство в лаборатории тестирования для добавления политики управления (MAM) Командной мобильное приложение Microsoft 365 dev/тестовой среды.'
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188157"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="bb934-103">Политики MAM для вашей среды разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="bb934-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="bb934-104">**Сводка:** Используйте в этом документе Test Lab Guide для добавления политики управления (MAM) Командной мобильное приложение Microsoft 365 dev/тестовой среды.</span><span class="sxs-lookup"><span data-stu-id="bb934-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="bb934-p101">Microsoft Enterprise мобильности + безопасности (Командной) помогает обеспечить вашим сотрудникам производительность пользователей с помощью своих избранные приложения и устройства защиты данных предприятия. Для получения дополнительных сведений см [мобильности Enterprise + безопасности (Командной)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="bb934-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="bb934-107">Согласно инструкциям в этой статье добавьте политик управления (MAM) мобильное приложение Microsoft 365 dev/тестовой среды.</span><span class="sxs-lookup"><span data-stu-id="bb934-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="bb934-108">Этап 1: Создание в работе Microsoft 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="bb934-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="bb934-109">Следуйте инструкциям в [Microsoft 365 Enterprise dev/тестовой среды](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="bb934-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="bb934-110">Этап 2. Создание и развертывание политики MAM для устройств с ОС iOS и Android</span><span class="sxs-lookup"><span data-stu-id="bb934-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="bb934-111">На этом этапе можно создать и развернуть две разные политики MAM отдельно для устройств с iOS и устройств Android.</span><span class="sxs-lookup"><span data-stu-id="bb934-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="bb934-112">Последовательно выберите пункты портала Office 365 ([https://portal.office.com](https://portal.office.com)) и войти в систему с учетной записью глобального администратора пробной подписки Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb934-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="bb934-113">На новой вкладке браузере откройте Azure портал ([https://azure.portal.com](https://azure.portal.com)) и выполнить вход с помощью учетной записи глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb934-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="bb934-114">Вкладки Azure портала в Internet Explorer, в области навигации щелкните **все службы**, введите **Intune**и нажмите кнопку **Intune**.</span><span class="sxs-lookup"><span data-stu-id="bb934-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **All services**, type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="bb934-115">В области навигации слева выберите раздел **Группы**.</span><span class="sxs-lookup"><span data-stu-id="bb934-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="bb934-116">На blade **групп все группы** нажмите кнопку **+ Новая группа**.</span><span class="sxs-lookup"><span data-stu-id="bb934-116">On the **Groups-All groups** blade, click **+ New Group**.</span></span>
    
6. <span data-ttu-id="bb934-117">На blade **группы** , выберите **Office 365** для **группу, тип?** введите **управляемых пользователей устройств операций ввода-вывода** в поле **имя**выберите **назначено** в **типа участия**и затем нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-117">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span> 
    
7. <span data-ttu-id="bb934-118">Закройте вкладку **Группа**.</span><span class="sxs-lookup"><span data-stu-id="bb934-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="bb934-119">На blade **групп все группы** нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="bb934-119">On the **Groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="bb934-120">На blade **группы** , выберите **Office 365** для **группу, тип?**, введите **управляемых Android устройство пользователя** в поле **имя**выберите **назначено** в **типа участия**и затем нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-120">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed Android device user** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span>
    
10. <span data-ttu-id="bb934-121">Закройте blade **групп все группы** .</span><span class="sxs-lookup"><span data-stu-id="bb934-121">Close the **Groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="bb934-122">В колонке **Intune**, в списке **Быстрые задачи**, выберите **Создайте политику соответствия**.</span><span class="sxs-lookup"><span data-stu-id="bb934-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="bb934-123">В колонке **Профили политики соответствия** нажмите **Создать политику**.</span><span class="sxs-lookup"><span data-stu-id="bb934-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="bb934-p102">В колонке **Создание политики**, в строке **Имя**, введите **iOS**. В разделе **Платформа** выберите **iOS**, нажмите **ОК** в колонке **Политика соответствия для iOS**, а затем нажмите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="bb934-126">В колонке **Профили политики соответствия** нажмите **Создать политику**.</span><span class="sxs-lookup"><span data-stu-id="bb934-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="bb934-p103">В колонке **Создание политики**, в строке **Имя**, введите **Android**. В разделе **Платформа** выберите **Android**, нажмите **ОК** в колонке **Политика соответствия для Android**, а затем нажмите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="bb934-129">В колонке **Профили политики соответствия** щелкните имя политики **Android**.</span><span class="sxs-lookup"><span data-stu-id="bb934-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="bb934-130">В колонке **Android — Свойства**, в левой области навигации, нажмите **Назначения** > **Выбрать группы**.</span><span class="sxs-lookup"><span data-stu-id="bb934-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="bb934-131">В колонке **Выбор групп** выберите группу **Управляемые пользователи устройств Android** и нажмите **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="bb934-132">Нажмите кнопку **Сохранить**, а затем закройте blade **Android - назначений** .</span><span class="sxs-lookup"><span data-stu-id="bb934-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="bb934-133">В колонке **Профили политики соответствия** щелкните имя политики **iOS**.</span><span class="sxs-lookup"><span data-stu-id="bb934-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="bb934-134">В колонке **iOS — Свойства**, в левой области навигации, нажмите **Назначения** > **Выбрать группы**.</span><span class="sxs-lookup"><span data-stu-id="bb934-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="bb934-135">В колонке **Выбор групп** выберите группу **Управляемые пользователи устройств iOS** и нажмите **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="bb934-136">Нажмите кнопку **Сохранить**, а затем закройте blade **iOS - назначений** .</span><span class="sxs-lookup"><span data-stu-id="bb934-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="bb934-137">Закройте колонку **Профили политики соответствия**.</span><span class="sxs-lookup"><span data-stu-id="bb934-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="bb934-138">В колонке **Intune** нажмите **Управление приложениями** в левой области навигации.</span><span class="sxs-lookup"><span data-stu-id="bb934-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="bb934-139">В колонке **Мобильные приложения** нажмите **Приложения**.</span><span class="sxs-lookup"><span data-stu-id="bb934-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="bb934-140">В списке приложений выберите **PowerPoint**. </span><span class="sxs-lookup"><span data-stu-id="bb934-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="bb934-p104">В колонке **PowerPoint — Обзор** нажмите **Назначения > Выбрать группы > Управляемые устройства iOS > Выбрать**. В разделе **Тип** выберите **Доступные** и нажмите **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="bb934-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="bb934-143">Повторите шаг 28 для следующих приложений:</span><span class="sxs-lookup"><span data-stu-id="bb934-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="bb934-144">Outlook для Android</span><span class="sxs-lookup"><span data-stu-id="bb934-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="bb934-145">Word для iOS</span><span class="sxs-lookup"><span data-stu-id="bb934-145">Word for iOS</span></span>
    
  - <span data-ttu-id="bb934-146">Excel для iOS</span><span class="sxs-lookup"><span data-stu-id="bb934-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="bb934-147">Outlook для iOS</span><span class="sxs-lookup"><span data-stu-id="bb934-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="bb934-148">Microsoft Dynamics CRM на iPad для iOS</span><span class="sxs-lookup"><span data-stu-id="bb934-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="bb934-149">Microsoft Dynamics CRM на iPhone для iOS</span><span class="sxs-lookup"><span data-stu-id="bb934-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="bb934-150">Dynamics CRM для телефонов для Android</span><span class="sxs-lookup"><span data-stu-id="bb934-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="bb934-151">Dynamics CRM для планшетов для Android</span><span class="sxs-lookup"><span data-stu-id="bb934-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="bb934-152">Excel для Android</span><span class="sxs-lookup"><span data-stu-id="bb934-152">Excel for Android</span></span>
    
  - <span data-ttu-id="bb934-153">Word для Android</span><span class="sxs-lookup"><span data-stu-id="bb934-153">Word for Android</span></span>
    
  - <span data-ttu-id="bb934-154">OneNote для iOS</span><span class="sxs-lookup"><span data-stu-id="bb934-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="bb934-155">Закройте вкладку **Мобильные приложения — Приложения**.</span><span class="sxs-lookup"><span data-stu-id="bb934-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="bb934-156">В колонке **Мобильные приложения** нажмите **Политики защиты приложений**.</span><span class="sxs-lookup"><span data-stu-id="bb934-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="bb934-157">В колонке **Политики защиты приложений** нажмите **Добавить политику**.</span><span class="sxs-lookup"><span data-stu-id="bb934-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="bb934-158">В колонке **Добавление политики** введите **iOS** и нажмите **Выбрать необходимые приложения**.</span><span class="sxs-lookup"><span data-stu-id="bb934-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="bb934-159">В колонке **Приложения** выберите **PowerPoint**, **Microsoft Dynamics CRM на iPhone**, **Excel**, **Microsoft Dynamics CRM на iPhone**, **Word**, **OneNote** и **Outlook** и нажмите **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="bb934-160">В колонке **Добавление политики** нажмите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="bb934-161">В колонке **Политики защиты приложений** нажмите **Добавить политику**.</span><span class="sxs-lookup"><span data-stu-id="bb934-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="bb934-162">В колонке **Добавление политики** введите **Android**, выберите **Android** в разделе **Платформа** и нажмите **Выбрать необходимые приложения**.</span><span class="sxs-lookup"><span data-stu-id="bb934-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="bb934-163">В колонке **Приложения** выберите **PowerPoint**, **Dynamics CRM для планшетов**, **Excel**, **Word**, **Outlook** и **Dynamics CRM для телефонов** и нажмите **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="bb934-164">В колонке **Добавление политики** нажмите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="bb934-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="bb934-165">Вы создали две отдельные политики MAM для устройств с ОС iOS и устройств с ОС Android и теперь можете поэкспериментировать с тестированием параметров для выбранных приложений.</span><span class="sxs-lookup"><span data-stu-id="bb934-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="bb934-166">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="bb934-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bb934-167">См. также</span><span class="sxs-lookup"><span data-stu-id="bb934-167">See Also</span></span>

[<span data-ttu-id="bb934-168">Среда разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="bb934-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="bb934-169">Регистрация устройств на базе ОС iOS и Android в среде разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="bb934-169">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="bb934-170">Руководства по созданию сред разработки и тестирования облачных решений</span><span class="sxs-lookup"><span data-stu-id="bb934-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="bb934-171">Мобильные решения на предприятиях + безопасности (Командной)</span><span class="sxs-lookup"><span data-stu-id="bb934-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


