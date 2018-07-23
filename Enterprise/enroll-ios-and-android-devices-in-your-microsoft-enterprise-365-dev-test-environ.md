---
title: Регистрация устройств на базе ОС iOS и Android в среде разработки и тестирования Microsoft 365 корпоративный
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Сводка: Используйте в этом документе Test Lab Guide Регистрация устройств в среде разработки и тестирования Microsoft 365 и удаленного управления.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720415"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="066e1-103">Регистрация устройств на базе ОС iOS и Android в среде разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="066e1-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="066e1-104">**Сводка:** В этом документе Test Lab Guide используйте для регистрации устройств в среде разработки и тестирования Microsoft 365 и удаленного управления.</span><span class="sxs-lookup"><span data-stu-id="066e1-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="066e1-p101">Microsoft Enterprise мобильности Suite Командной помогает обеспечить вашим сотрудникам производительность пользователей с помощью своих избранные приложения и устройства защиты данных предприятия. Для получения дополнительных сведений см [мобильности Enterprise + безопасности (Командной)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="066e1-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="066e1-p102">Если требуется применить защиту на уровне устройства, необходимо зарегистрировать устройств в Microsoft Intune. Регистрация устройств не только помогает управлять во владении организации устройств, но также личный (BYOD) и общих устройств, в зависимости от организации в юридических политик.</span><span class="sxs-lookup"><span data-stu-id="066e1-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="066e1-109">Выполнив инструкции, приведенные в этой статье, вы сможете регистрация и проверка возможности управления базовой мобильного устройства для iOS и Android в среде разработки и тестирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="066e1-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="066e1-110">Этап 1: Создание Microsoft 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="066e1-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="066e1-111">Следуйте инструкциям в [Microsoft 365 Enterprise dev/тестовой среды](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="066e1-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="066e1-112">Этап 2: Регистрация операций ввода-вывода и Android</span><span class="sxs-lookup"><span data-stu-id="066e1-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="066e1-113">Во-первых, используйте инструкции в [установки и войдите в приложение портала компании](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) для настройки приложения портала компании Майкрософт Intune для тестовой среды.</span><span class="sxs-lookup"><span data-stu-id="066e1-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="066e1-114">Затем используйте инструкции из статьи [Настройка доступа к ресурсам компании](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) для подачи заявок на устройстве операций ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="066e1-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="066e1-115">Затем используйте инструкции из статьи [Заявка Android устройство в Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) возможность зачисления Android устройства.</span><span class="sxs-lookup"><span data-stu-id="066e1-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="066e1-116">Этап 3: IOS и Android удаленного управления</span><span class="sxs-lookup"><span data-stu-id="066e1-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="066e1-p103">Microsoft Intune предоставляет удаленного блокировки и код связи для сброса возможности. Если кто-то теряет свои устройства, можно заблокировать устройство удаленно. Если кто-то забудет их код связи, ее можно восстановить удаленно.</span><span class="sxs-lookup"><span data-stu-id="066e1-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="066e1-120">Чтобы заблокировать операций ввода-вывода или Android устройство удаленно:</span><span class="sxs-lookup"><span data-stu-id="066e1-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="066e1-121">Войдите в портал Azure в [https://portal.azure.com](https://portal.azure.com) с использованием учетных данных учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="066e1-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="066e1-122">Выберите **все службы**, введите **Intune**и нажмите кнопку **Intune**.</span><span class="sxs-lookup"><span data-stu-id="066e1-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="066e1-123">Нажмите кнопку **устройства > все устройства**.</span><span class="sxs-lookup"><span data-stu-id="066e1-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="066e1-124">В списке устройств нажмите кнопку операций ввода-вывода или Android устройства и нажмите кнопку действие **удаленного блокировки** .</span><span class="sxs-lookup"><span data-stu-id="066e1-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="066e1-125">Чтобы удаленно сбросить секретный код, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="066e1-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="066e1-126">При необходимости, войдите в портал Azure в [https://portal.azure.com](https://portal.azure.com) с использованием учетных данных учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="066e1-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="066e1-127">Выберите **все службы**, введите **Intune**и нажмите кнопку **Intune**.</span><span class="sxs-lookup"><span data-stu-id="066e1-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="066e1-128">Нажмите кнопку **устройства > все устройства**.</span><span class="sxs-lookup"><span data-stu-id="066e1-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="066e1-p104">В списке устройств, управление, щелкните операций ввода-вывода или Android устройство и выберите **... Дополнительные**. Выберите действие удаленных устройств **Удалить секретный код** .</span><span class="sxs-lookup"><span data-stu-id="066e1-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="066e1-131">Дополнительные экспериментов в разделе [действия из доступных устройств](https://docs.microsoft.com/intune/device-management#available-device-actions).</span><span class="sxs-lookup"><span data-stu-id="066e1-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="066e1-132">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="066e1-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="066e1-133">См. также</span><span class="sxs-lookup"><span data-stu-id="066e1-133">See Also</span></span>

[<span data-ttu-id="066e1-134">Среда разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="066e1-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="066e1-135">Политики MAM для вашей среды разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="066e1-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="066e1-136">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="066e1-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="066e1-137">Мобильные решения на предприятиях + безопасности (Командной)</span><span class="sxs-lookup"><span data-stu-id="066e1-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


