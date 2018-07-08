---
title: Регистрация устройств на базе ОС iOS и Android в среде разработки и тестирования Microsoft 365 корпоративный
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Сводка: Используйте в этом документе Test Lab Guide Регистрация устройств в среде разработки и тестирования Microsoft 365 и удаленного управления.'
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188107"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="754b2-103">Регистрация устройств на базе ОС iOS и Android в среде разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="754b2-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="754b2-104">**Сводка:** В этом документе Test Lab Guide используйте для регистрации устройств в среде разработки и тестирования Microsoft 365 и удаленного управления.</span><span class="sxs-lookup"><span data-stu-id="754b2-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="754b2-p101">Microsoft Enterprise мобильности Suite Командной помогает обеспечить вашим сотрудникам производительность пользователей с помощью своих избранные приложения и устройства защиты данных предприятия. Для получения дополнительных сведений см [мобильности Enterprise + безопасности (Командной)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="754b2-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="754b2-p102">Если требуется применить защиту на уровне устройства, необходимо зарегистрировать устройств в Microsoft Intune. Регистрация устройств не только помогает управлять во владении организации устройств, но также личный (BYOD) и общих устройств, в зависимости от организации в юридических политик.</span><span class="sxs-lookup"><span data-stu-id="754b2-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="754b2-109">Выполнив инструкции, приведенные в этой статье, вы сможете регистрация и проверка возможности управления базовой мобильного устройства для iOS и Android в среде разработки и тестирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="754b2-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="754b2-110">Этап 1: Создание Microsoft 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="754b2-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="754b2-111">Следуйте инструкциям в [Microsoft 365 Enterprise dev/тестовой среды](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="754b2-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="754b2-112">Этап 2: Регистрация операций ввода-вывода и Android</span><span class="sxs-lookup"><span data-stu-id="754b2-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="754b2-113">Во-первых, используйте инструкции в [установки и войдите в приложение портала компании](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) для настройки приложения портала компании Майкрософт Intune для вашего клиента разработку и тестирование.</span><span class="sxs-lookup"><span data-stu-id="754b2-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="754b2-114">Затем используйте инструкции из статьи [Настройка доступа к ресурсам компании](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) для подачи заявок на устройстве операций ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="754b2-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="754b2-115">Затем используйте инструкции из статьи [Заявка Android устройство в Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) возможность зачисления Android устройства.</span><span class="sxs-lookup"><span data-stu-id="754b2-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="754b2-116">Этап 2: IOS и Android удаленного управления</span><span class="sxs-lookup"><span data-stu-id="754b2-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="754b2-p103">Microsoft Intune предоставляет возможности удаленной блокировки и сброса секретного кода. Если пользователь потеряет свое устройство, вы можете заблокировать это устройство удаленно. Если пользователь забудет свой секретный код, вы можете удаленно сбросить этот код.</span><span class="sxs-lookup"><span data-stu-id="754b2-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="754b2-120">Чтобы удаленно заблокировать устройство с iOS:</span><span class="sxs-lookup"><span data-stu-id="754b2-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="754b2-121">Откройте новую вкладку и перейдите к http://manage.microsoft.com (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="754b2-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="754b2-122">В консоли администрирования Microsoft Intune браузера щелкните **группы** в левой панели навигации.</span><span class="sxs-lookup"><span data-stu-id="754b2-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="754b2-123">В области **Группы** откройте раздел **Все устройства > Все мобильные устройства > Все устройства с прямым управлением**.</span><span class="sxs-lookup"><span data-stu-id="754b2-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="754b2-124">В области **Все устройства с прямым управлением** откройте вкладку **Устройства**.</span><span class="sxs-lookup"><span data-stu-id="754b2-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="754b2-125">Выберите свое устройство с iOS в списке. </span><span class="sxs-lookup"><span data-stu-id="754b2-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="754b2-126">Убедитесь, что на устройстве с iOS открыт главный экран. </span><span class="sxs-lookup"><span data-stu-id="754b2-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="754b2-p104">На компьютере администратора выберите на панели задач пункты **Удаленные задачи > Удаленная блокировка**. Наблюдайте, как устройство с iOS переключается на экран блокировки.</span><span class="sxs-lookup"><span data-stu-id="754b2-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="754b2-129">Чтобы удалить секретный код:</span><span class="sxs-lookup"><span data-stu-id="754b2-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="754b2-130">На компьютере администратора найдите область **Все устройства с прямым управлением** и откройте вкладку **Устройства**.</span><span class="sxs-lookup"><span data-stu-id="754b2-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="754b2-p105">Выберите свое устройство с iOS в списке. Выберите на панели задач пункты **Удаленные задачи > Сброс секретного кода**. Подождите минуту.</span><span class="sxs-lookup"><span data-stu-id="754b2-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="754b2-p106">Разблокируйте устройство с iOS и обратите внимание, что секретный код удален. Чтобы снова назначить секретный код, откройте раздел **Настройки** и выберите **Секретный код**.</span><span class="sxs-lookup"><span data-stu-id="754b2-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="754b2-136">Чтобы удаленно заблокировать устройство с Android:</span><span class="sxs-lookup"><span data-stu-id="754b2-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="754b2-137">В консоли администрирования Microsoft Intune браузера щелкните **группы** в левой панели навигации.</span><span class="sxs-lookup"><span data-stu-id="754b2-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="754b2-138">В области **Группы** откройте раздел **Все устройства > Все мобильные устройства > Все устройства с прямым управлением**.</span><span class="sxs-lookup"><span data-stu-id="754b2-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="754b2-139">В области **Все устройства с прямым управлением** откройте вкладку **Устройства**.</span><span class="sxs-lookup"><span data-stu-id="754b2-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="754b2-140">Выберите свое устройство с Android в списке устройств. </span><span class="sxs-lookup"><span data-stu-id="754b2-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="754b2-141">Убедитесь, что на устройстве с Android открыт главный экран. </span><span class="sxs-lookup"><span data-stu-id="754b2-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="754b2-p107">На компьютере администратора выберите на панели задач пункты **Удаленные задачи > Удаленная блокировка**. При появлении соответствующего запроса нажмите кнопку **Да**.</span><span class="sxs-lookup"><span data-stu-id="754b2-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="754b2-144">Наблюдайте, как устройство с Android переключается на экран блокировки.</span><span class="sxs-lookup"><span data-stu-id="754b2-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="754b2-145">При сбросе секретный код для Android устройств портала администрирования Intune создает и настраивает строгое секретный код.</span><span class="sxs-lookup"><span data-stu-id="754b2-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="754b2-146">Чтобы удаленно сбросить секретный код, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="754b2-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="754b2-147">На компьютере администратора откройте в браузере вкладку консоли администрирования Microsoft Intune и выберите свое устройство с Android в области **Все устройства с прямым управлением**.</span><span class="sxs-lookup"><span data-stu-id="754b2-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="754b2-148">Выберите на панели задач пункты **Удаленные задачи > Сброс секретного кода**.</span><span class="sxs-lookup"><span data-stu-id="754b2-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="754b2-p108">В окне **Удаленная задача. Сброс секретного кода** нажмите кнопку **Да**. Подождите минуту.</span><span class="sxs-lookup"><span data-stu-id="754b2-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="754b2-151">В области **Все устройства с прямым управлением** нажмите **Просмотреть свойства**.</span><span class="sxs-lookup"><span data-stu-id="754b2-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="754b2-152">Запишите новый секретный код из раздела **Сброс секретного кода**.</span><span class="sxs-lookup"><span data-stu-id="754b2-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="754b2-153">Введите этот код на экране блокировки устройства с Android. </span><span class="sxs-lookup"><span data-stu-id="754b2-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="754b2-154">Чтобы восстановить секретный код, откройте **Настройки**, выберите раздел **Устройство**, затем **Экран блокировки**, снова введите новый секретный код, нажмите **Блокировка экрана**, а затем введите нужный секретный код.</span><span class="sxs-lookup"><span data-stu-id="754b2-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="754b2-155">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="754b2-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="754b2-156">См. также</span><span class="sxs-lookup"><span data-stu-id="754b2-156">See Also</span></span>

[<span data-ttu-id="754b2-157">Среда разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="754b2-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="754b2-158">Политики MAM для вашей среды разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="754b2-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="754b2-159">Руководства по созданию сред разработки и тестирования облачных решений</span><span class="sxs-lookup"><span data-stu-id="754b2-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="754b2-160">Мобильные решения на предприятиях + безопасности (Командной)</span><span class="sxs-lookup"><span data-stu-id="754b2-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


