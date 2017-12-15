---
title: "Регистрация операций ввода-вывода и Android в среде разработки и тестирования Microsoft Enterprise 365"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Сводка: Используйте в этом документе Test Lab Guide Регистрация устройств в среде разработки и тестирования Microsoft 365 и удаленного управления."
ms.openlocfilehash: 8ad22ed62d8e7cac8aca225af42e389dc05cb2b5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="d39ca-103">Регистрация операций ввода-вывода и Android в среде разработки и тестирования Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="d39ca-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="d39ca-104">**Сводка:** В этом документе Test Lab Guide используйте для регистрации устройств в среде разработки и тестирования Microsoft 365 и удаленного управления.</span><span class="sxs-lookup"><span data-stu-id="d39ca-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="d39ca-p101">Microsoft Enterprise мобильности Suite Командной помогает обеспечить вашим сотрудникам производительность пользователей с помощью своих избранные приложения и устройства защиты данных предприятия. Для получения дополнительных сведений см [мобильности Enterprise + безопасности (Командной)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="d39ca-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="d39ca-p102">Чтобы применить защиту на уровне устройств, необходимо зарегистрировать их в Microsoft Intune. Регистрация устройств помогает управлять не только корпоративными, но и личными и общими устройствами (в зависимости от правовых политик организации).</span><span class="sxs-lookup"><span data-stu-id="d39ca-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="d39ca-109">Выполнив инструкции, приведенные в этой статье, вы сможете регистрация и проверка возможности управления базовой мобильного устройства для iOS и Android в среде разработки и тестирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d39ca-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="d39ca-110">Этап 1: Создание Microsoft 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="d39ca-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="d39ca-111">Следуйте инструкциям в [Microsoft 365 Enterprise dev/тестовой среды](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d39ca-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="d39ca-112">Этап 2. Настройка приложения "Корпоративный портал Microsoft Intune"</span><span class="sxs-lookup"><span data-stu-id="d39ca-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="d39ca-113">Выполните указанные ниже действия, чтобы настроить приложение корпоративного портала Microsoft Intune для вымышленной компании.</span><span class="sxs-lookup"><span data-stu-id="d39ca-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="d39ca-114">На новой вкладке откройте консоль администрирования Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).</span><span class="sxs-lookup"><span data-stu-id="d39ca-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="d39ca-115">На левой панели навигации щелкните **Администрирование** и нажмите кнопку **Мобильного устройства управления** на панели **администрирования** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="d39ca-p103">В списке **задач** выберите **Задать центра управления мобильного устройства**. Убедитесь, что оно задано значение **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="d39ca-118">На панели **администрирования** щелкните **Портала компании**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="d39ca-119">В области **Портала компании** настройте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="d39ca-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="d39ca-120">Название компании: \<название вымышленной компании ></span><span class="sxs-lookup"><span data-stu-id="d39ca-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="d39ca-121">Имя контакта отдел ИТ: **User5**</span><span class="sxs-lookup"><span data-stu-id="d39ca-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="d39ca-122">Номер телефона отдел ИТ: **555-1234**</span><span class="sxs-lookup"><span data-stu-id="d39ca-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="d39ca-123">Адрес электронной почты отдела ИТ: **User5 @**\<название вымышленной организации > **. onmicrosoft.com** (адрес электронной почты учетной записи User5)</span><span class="sxs-lookup"><span data-stu-id="d39ca-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="d39ca-124">В **настройке**выберите **зеленый** цвет **темы**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="d39ca-125">Нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-125">Click **Save**.</span></span>
    
<span data-ttu-id="d39ca-126">Теперь установите приложение "Корпоративный портал Microsoft Intune" и зарегистрируйте устройство с iOS или Android, а затем испытайте основные функции управления с помощью консоли администрирования Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="d39ca-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="d39ca-127">Этап 3 (только для устройств с iOS). Регистрация устройства с iOS и управление им</span><span class="sxs-lookup"><span data-stu-id="d39ca-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="d39ca-128">Чтобы зарегистрировать устройство с iOS для управления с помощью Intune, вам потребуется следующее:</span><span class="sxs-lookup"><span data-stu-id="d39ca-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="d39ca-129">Устройство с iOS, например Apple iPad или iPhone.</span><span class="sxs-lookup"><span data-stu-id="d39ca-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="d39ca-130">Знание секретный код устройства операций ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="d39ca-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="d39ca-p104">Идентификатор Apple (имя учетной записи и пароль). Если вы не сделали этого, перейдите на [веб-сайте Apple код](https://appleid.apple.com/#!&amp;page=signin) и нажмите кнопку **Создать код Apple**. Создайте идентификатор Apple, соответствующий учетной записи глобального администратора подписки Office 365. Запишите новый идентификатор Apple имя учетной записи и пароль в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="d39ca-p105">Для управления компьютерами Mac и устройствами с iOS с помощью Intune необходим сертификат службы push-уведомлений Apple (APNs). После добавления сертификата в Intune пользователи могут установить приложение "Корпоративный портал Microsoft Intune", чтобы зарегистрировать свои устройства, либо администратор может настроить управление корпоративными устройствами с iOS.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="d39ca-p106">Чтобы запросить сертификат отношения доверия с портала сертификатов Apple Push, необходим файл запроса подписи сертификата. Чтобы получить файл запроса подписи сертификата:</span><span class="sxs-lookup"><span data-stu-id="d39ca-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="d39ca-139">В консоли администрирования Microsoft Intune щелкните **Администрирование** на левой панели навигации.</span><span class="sxs-lookup"><span data-stu-id="d39ca-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="d39ca-140">На панели **администрирования** откройте **управления мобильные устройства > операций ввода-вывода и Mac OS X**и нажмите кнопку **отправить сертификат APN** в **задачах**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="d39ca-p107">На левой панели **отправить сертификат APN** нажмите кнопку **загрузить APN запроса на сертификат**. Сохраните файл запроса (.csr) локально с именем **dev test**подписи сертификата.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="d39ca-143">Чтобы получить сертификат службы push-уведомлений Apple, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="d39ca-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="d39ca-144">Откройте новую вкладку, перейдите к [Apple Push-сертификаты портала](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)и вход с помощью Apple идентификатор.</span><span class="sxs-lookup"><span data-stu-id="d39ca-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="d39ca-145">На странице " **Начало работы** " нажмите кнопку **создать сертификат**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="d39ca-146">На странице **Условий использования** выберите **я прочитал(а) и согласны с эти условия**и нажмите кнопку **принять**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="d39ca-p108">На странице **Создание нового сертификата Push-** нажмите кнопку **Обзор** , выберите файл **test.csr разработчиков** , сохраненный в предыдущей процедуре и нажмите кнопку **Отправить**. При отображении запроса на открытие файла json, сохраните его в ту же папку, где хранится файл test.csr разработчиков.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="d39ca-149">Откройте [Apple Push-сертификаты портала](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) в новой вкладки и **сертификатов для серверов сторонних производителей**, нажмите кнопку **загрузить**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="d39ca-p109">При отображении запроса на открытие файла .pem, сохраните его с имя **test.pem разработчиков** в ту же папку, где хранится файл test.csr разработчиков. Это APN сертификата.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="d39ca-152">Чтобы отправить сертификат APNs в Intune:</span><span class="sxs-lookup"><span data-stu-id="d39ca-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="d39ca-153">На вкладке консоль Microsoft Intune администрирования на странице " **отправить сертификат APN** " щелкните **Отправить APN сертификата**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="d39ca-154">Нажмите кнопку **Обзор** и укажите файл **test.pem разработчиков** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="d39ca-p110">Нажмите кнопку **Открыть**, введите имя своей учетной записи Apple код и нажмите кнопку **Отправить**. Должно появиться сообщение **Готово для регистрации** на странице **операций ввода-вывода и настройка управления MaxOS X мобильного устройства** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="d39ca-157">После установки сертификата APNs Intune может регистрировать устройства с iOS и управлять ими, применяя политику к зарегистрированным мобильным устройствам.</span><span class="sxs-lookup"><span data-stu-id="d39ca-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="d39ca-158">Чтобы скачать приложение "Корпоративный портал Microsoft Intune" и зарегистрировать устройство с iOS:</span><span class="sxs-lookup"><span data-stu-id="d39ca-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="d39ca-159">На устройстве с iOS выполните вход с помощью своего идентификатора Apple ID.</span><span class="sxs-lookup"><span data-stu-id="d39ca-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="d39ca-160">Откройте приложение **Магазина Apple** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="d39ca-161">В поле «Поиск» введите **intune** и коснитесь **Портал Intune компании Microsoft**, затем **получить**и **установить**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="d39ca-162">После завершения установки, выберите команду **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="d39ca-163">На экране **Портала компании Intune** вход с помощью учетной записи глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="d39ca-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="d39ca-164">На странице **Настройка доступа к компании** выберите **Начать**и дважды нажмите кнопку **Продолжить** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="d39ca-165">На **что идет дальше?** экрана, коснитесь **Заявка**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="d39ca-166">На **администратора активировать устройство?** экрана, выберите **активировать**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="d39ca-167">На экране **Профиля управления** выберите **Установка**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="d39ca-168">В **Введите код связи**введите ваш код связи устройства операций ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="d39ca-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="d39ca-169">На экран **что идет дальше** нажмите кнопку **Регистрация**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="d39ca-170">В **Установка профиля**нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="d39ca-171">На странице **Предупреждение** нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="d39ca-172">**Удаленное управление**коснитесь **доверия**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="d39ca-173">Нажмите кнопку **Готово** для завершения процесса регистрации.</span><span class="sxs-lookup"><span data-stu-id="d39ca-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="d39ca-174">При отображении запроса на **Открыть эту страницу «Comp Portal»?**, выберите команду **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="d39ca-175">На странице **Настройка доступа к компании** выберите **Начать**и нажмите кнопку « **Готово**».</span><span class="sxs-lookup"><span data-stu-id="d39ca-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="d39ca-176">На главном экране приложения "Корпоративный портал Microsoft Intune" должны отображаться следующие элементы:</span><span class="sxs-lookup"><span data-stu-id="d39ca-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="d39ca-177">Зеленый баннер.</span><span class="sxs-lookup"><span data-stu-id="d39ca-177">A green banner.</span></span>
    
  - <span data-ttu-id="d39ca-178">Название вымышленной компании в левом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="d39ca-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="d39ca-179">Имя устройства операций ввода-вывода, перечисленные в **Личных устройств**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="d39ca-180">В разделе **Служба технической поддержки** **Имя контакта** **User5** с номером телефона **555-1234** и кнопку **контакта по адресу электронной почты** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="d39ca-p111">Microsoft Intune предоставляет возможности удаленной блокировки и сброса секретного кода. Если пользователь потеряет свое устройство, вы можете заблокировать это устройство удаленно. Если пользователь забудет свой секретный код, вы можете удаленно сбросить этот код.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="d39ca-184">Чтобы удаленно заблокировать устройство с iOS:</span><span class="sxs-lookup"><span data-stu-id="d39ca-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="d39ca-185">С компьютера администрирования на вкладке консоли администрирования Microsoft Intune браузера щелкните **группы** в левой панели навигации.</span><span class="sxs-lookup"><span data-stu-id="d39ca-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="d39ca-186">Откройте в области **группы** **все устройства > все мобильные устройства > все прямое устройства управляемых**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="d39ca-187">В области **Все прямое устройства,** перейдите на вкладку **устройств** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="d39ca-188">Выберите свое устройство с iOS в списке. </span><span class="sxs-lookup"><span data-stu-id="d39ca-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="d39ca-189">Убедитесь, что на устройстве с iOS открыт главный экран. </span><span class="sxs-lookup"><span data-stu-id="d39ca-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="d39ca-p112">С компьютера администрирования на панели задач нажмите кнопку **удаленной задачи > удаленного блокировки**. Следите за устройства iOS переключится на экран блокировки.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="d39ca-192">Чтобы удалить секретный код:</span><span class="sxs-lookup"><span data-stu-id="d39ca-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="d39ca-193">С компьютера администрирования в области **Все прямое устройства,** перейдите на вкладку **устройств** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="d39ca-p113">В списке выберите устройство операций ввода-вывода. На панели задач нажмите кнопку **удаленной задачи > Сброс секретный код**. Подождите одну минуту.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="d39ca-p114">С устройства iOS его разблокирования и обратите внимание на то, что оно больше не код связи. Чтобы изменить секретный код обратно, перейдите в **Параметры**, а затем **код связи**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="d39ca-199">Этап 3 (только для устройств с Android). Регистрация устройства с Android и управление им</span><span class="sxs-lookup"><span data-stu-id="d39ca-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="d39ca-200">Чтобы зарегистрировать устройство с Android для управления с помощью Intune, вам потребуется следующее:</span><span class="sxs-lookup"><span data-stu-id="d39ca-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="d39ca-201">Устройство с Android.</span><span class="sxs-lookup"><span data-stu-id="d39ca-201">An Android device.</span></span>
    
- <span data-ttu-id="d39ca-202">Знание секретный код устройства.</span><span class="sxs-lookup"><span data-stu-id="d39ca-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="d39ca-203">Чтобы скачать приложение "Корпоративный портал Intune" и зарегистрировать устройство с Android:</span><span class="sxs-lookup"><span data-stu-id="d39ca-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="d39ca-204">С устройства Android **Google воспроизвести хранилища**и нажмите кнопку « **Начало работы**».</span><span class="sxs-lookup"><span data-stu-id="d39ca-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="d39ca-205">В поле «Поиск» введите **intune** , а затем коснитесь **портала компании intune** в результатах поиска.</span><span class="sxs-lookup"><span data-stu-id="d39ca-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="d39ca-206">Коснитесь элемента **Портала компании Intune** и нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="d39ca-207">На экране **для завершения настройки учетной записи** выберите **Продолжить**и **Пропустить**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="d39ca-p115">**Портал компания Intune**нажмите **принято**. Установка приложения.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="d39ca-210">Выберите команду **Открыть**и нажмите кнопку « **войти**».</span><span class="sxs-lookup"><span data-stu-id="d39ca-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="d39ca-211">На экране **Портала компании Intune** вход с помощью учетной записи глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="d39ca-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="d39ca-212">На странице **Настройка доступа к компании** дважды коснитесь **Начать**и нажмите **Продолжить** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="d39ca-213">На **что идет дальше?** экрана, коснитесь **Заявка**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="d39ca-214">На **администратора активировать устройство?** экрана, коснитесь **Activate.**</span><span class="sxs-lookup"><span data-stu-id="d39ca-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="d39ca-p116">На экране **Политику конфиденциальности** выберите **я принимаю условия соглашения** и нажмите кнопку «» **Подтверждение**. Дождитесь завершения процесса регистрации.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="d39ca-217">На экране **Установки компании доступа** выберите **Продолжить**и нажмите кнопку « **Готово**».</span><span class="sxs-lookup"><span data-stu-id="d39ca-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="d39ca-218">На главном экране приложения "Корпоративный портал Microsoft Intune" должны отображаться зеленый баннер и название вымышленной компании в левом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="d39ca-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="d39ca-p117">Коснитесь **устройств**. Вы должны увидеть имя Android устройство в списке.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="d39ca-p118">Коснитесь **контакт ИТ**. Должно появиться номер телефона **555-1234**, кнопки **контактов по электронной почте** , и ИТ контактов из **User5**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="d39ca-p119">Microsoft Intune предоставляет возможности удаленной блокировки и сброса секретного кода. Если пользователь потеряет свое устройство, вы можете заблокировать это устройство удаленно. Если пользователь забудет свой секретный код, вы можете удаленно сбросить этот код.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="d39ca-226">Чтобы удаленно заблокировать устройство с Android:</span><span class="sxs-lookup"><span data-stu-id="d39ca-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="d39ca-227">С компьютера администрирования на вкладке консоли администрирования Microsoft Intune браузера щелкните **группы** в левой панели навигации.</span><span class="sxs-lookup"><span data-stu-id="d39ca-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="d39ca-228">Откройте в области **группы** **все устройства > все мобильные устройства > все прямое устройства управляемых**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="d39ca-229">В области **Все прямое устройства,** перейдите на вкладку **устройств** .</span><span class="sxs-lookup"><span data-stu-id="d39ca-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="d39ca-230">Выберите свое устройство с Android в списке устройств. </span><span class="sxs-lookup"><span data-stu-id="d39ca-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="d39ca-231">Убедитесь, что на устройстве с Android открыт главный экран. </span><span class="sxs-lookup"><span data-stu-id="d39ca-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="d39ca-p120">С компьютера администрирования на панели задач нажмите кнопку **удаленной задачи > удаленного блокировки**. При появлении запроса нажмите кнопку **Да**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="d39ca-234">Наблюдайте, как устройство с Android переключается на экран блокировки.</span><span class="sxs-lookup"><span data-stu-id="d39ca-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="d39ca-235">При сбросе секретный код для Android устройств портала администрирования Intune создает и настраивает строгое секретный код.</span><span class="sxs-lookup"><span data-stu-id="d39ca-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="d39ca-236">Чтобы удаленно сбросить секретный код, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="d39ca-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="d39ca-237">С компьютера администрирования на вкладке консоли администрирования Microsoft Intune браузера, в области **Все прямое устройства управляемых** выберите Android устройство.</span><span class="sxs-lookup"><span data-stu-id="d39ca-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="d39ca-238">На панели задач нажмите кнопку **удаленной задачи > Сброс секретный код**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="d39ca-p121">На **удаленной задачи: Reset секретный код** , нажмите кнопку **Да**. Подождите одну минуту.</span><span class="sxs-lookup"><span data-stu-id="d39ca-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="d39ca-241">В области **Все прямое устройства,** щелкните **Просмотреть свойства**.</span><span class="sxs-lookup"><span data-stu-id="d39ca-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="d39ca-242">В разделе **Reset секретный код**Обратите внимание на то новый код связи.</span><span class="sxs-lookup"><span data-stu-id="d39ca-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="d39ca-243">Введите этот код на экране блокировки устройства с Android. </span><span class="sxs-lookup"><span data-stu-id="d39ca-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="d39ca-244">Чтобы изменить секретный код обратно, перейдите к **параметрам**, коснитесь **устройства**, коснитесь **экран блокировки**, введите новый секретный код еще раз, коснитесь **экрана блокировки**и выбор для секретный код.</span><span class="sxs-lookup"><span data-stu-id="d39ca-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="d39ca-245">Щелкните [здесь](http://aka.ms/catlgstack) для visual карты для всех статей в стеке один Microsoft Cloud руководство по лаборатории тестирования.</span><span class="sxs-lookup"><span data-stu-id="d39ca-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d39ca-246">See Also</span><span class="sxs-lookup"><span data-stu-id="d39ca-246">See Also</span></span>

[<span data-ttu-id="d39ca-247">Microsoft 365 Enterprise dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="d39ca-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="d39ca-248">MAM политик для вашей среды разработки или тестирования Microsoft 365 для предприятия</span><span class="sxs-lookup"><span data-stu-id="d39ca-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="d39ca-249">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="d39ca-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="d39ca-250">Мобильные решения на предприятиях + безопасности (Командной)</span><span class="sxs-lookup"><span data-stu-id="d39ca-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


