---
title: "Многофакторная проверка подлинности для среды разработки и тестирования Office 365"
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
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- mar17entnews
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "Сводка: Настройка многофакторной проверки подлинности с помощью текста сообщения, отправленные на смарт-телефон в среде разработки и тестирования Office 365."
ms.openlocfilehash: 87fdcc2ccd910e8da399e14d37fe3d0d1f0a66d4
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="6ae16-103">Многофакторная проверка подлинности для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6ae16-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="6ae16-104">**Сводка:** Настройка многофакторной проверки подлинности с помощью текста сообщения, отправленные на смарт-телефон в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="6ae16-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="6ae16-p101">Чтобы установить дополнительный уровень защиты при входе в учетную запись Office 365, включите многофакторную проверку подлинности Azure. Если эта функция включена, после правильного ввода пароля пользователь должен будет ответить на телефонный звонок, ввести код проверки, отправленный в текстовом сообщении, или указать пароль приложения на смартфоне. Только после этого он сможет войти в свою учетную запись. </span><span class="sxs-lookup"><span data-stu-id="6ae16-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to verify an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="6ae16-108">В этой статье описано, как включить проверку подлинности на основе текстовых сообщений для учетной записи Office 365 и проверить ее работу.</span><span class="sxs-lookup"><span data-stu-id="6ae16-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="6ae16-109">Настройка многофакторной проверки подлинности для Office 365 в среде разработки и тестирования состоит из двух этапов:</span><span class="sxs-lookup"><span data-stu-id="6ae16-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="6ae16-110">Создание среды разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="6ae16-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="6ae16-111">Включение и проверка многофакторной проверки подлинности для учетной записи User 2.</span><span class="sxs-lookup"><span data-stu-id="6ae16-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="6ae16-112">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="6ae16-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="6ae16-113">Этап 1. Создание среды разработки и тестирования Office 365  упрощенной или для имитированных предприятий</span><span class="sxs-lookup"><span data-stu-id="6ae16-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="6ae16-114">Если необходимо проверить многофакторной проверки подлинности в облегченный путь с минимальным требованиям, следуйте инструкциям в этапы 2 и 3 [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6ae16-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="6ae16-115">Если вы хотите проверить многофакторной проверки подлинности в имитации enterprise, следуйте инструкциям в [DirSync для вашей среды разработки или тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6ae16-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="6ae16-p102">Для проверки не требуется условная корпоративная среда разработки и тестирования, которая включает условную интрасеть, подключенную к Интернету, и синхронизацию каталогов для леса Windows Server AD. Она показана здесь лишь для того, чтобы вы могли проверить многофакторную проверку подлинности и поэкспериментировать с этим компонентом в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="6ae16-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="6ae16-118">Этап 2. Включение и проверка многофакторной проверки подлинности для учетной записи User 2</span><span class="sxs-lookup"><span data-stu-id="6ae16-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="6ae16-119">Чтобы включить многофакторную проверку подлинности для учетной записи User 2, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="6ae16-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="6ae16-120">Открыть отдельный экземпляр браузера, перейдите к порталу Office 365 ([https://portal.office.com](https://portal.office.com)) и выполните вход на пробной подписки Office 365 с учетной записью глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="6ae16-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="6ae16-121">На главной странице портала щелкните **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="6ae16-122">На панели навигации слева выберите элементы **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="6ae16-123">В области активных пользователей щелкните **более > многофакторной проверкой подлинности на основе программы установки Azure**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-123">In the Active users pane, click **More > Setup Azure multi-factor auth**.</span></span>
    
5. <span data-ttu-id="6ae16-124">В списке щелкните учетную запись **пользователя 2** .</span><span class="sxs-lookup"><span data-stu-id="6ae16-124">In the list, click the **User 2** account.</span></span>
    
6. <span data-ttu-id="6ae16-125">В разделе **2 пользователя** в разделе **Быстрые действия**, нажмите кнопку **Включить**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="6ae16-126">В диалоговом окне **о включении многофакторной проверкой подлинности на основе** щелкните **Включение многофакторной проверкой подлинности на основе**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="6ae16-127">В диалоговом окне **успешное обновление** нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-127">In the **Update successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="6ae16-128">На вкладке **Microsoft Office для дома** щелкните значок учетной записи пользователя в правом верхнем углу и выберите команду **Выход**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="6ae16-129">Закройте окно браузера.</span><span class="sxs-lookup"><span data-stu-id="6ae16-129">Close your browser instance.</span></span>
    
<span data-ttu-id="6ae16-130">Чтобы настроить отправку текстового сообщения для проверки учетной записи User 2 и проверить ее, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="6ae16-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="6ae16-131">Откройте новое окно браузера.</span><span class="sxs-lookup"><span data-stu-id="6ae16-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="6ae16-132">Последовательно выберите пункты портала Office 365 ([https://portal.office.com](https://portal.office.com)) и входа в систему с учетной записью пользователя 2 (Пользователь2 @\<название организации >. onmicrosoft.com) и пароль.</span><span class="sxs-lookup"><span data-stu-id="6ae16-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="6ae16-p103">После входа в запрос для настройки учетной записи для проверки для обеспечения дополнительного уровня безопасности. Щелкните **его настройку**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="6ae16-135">На странице **проверки для обеспечения дополнительного уровня безопасности** :</span><span class="sxs-lookup"><span data-stu-id="6ae16-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="6ae16-136">Выберите свою страну или регион.</span><span class="sxs-lookup"><span data-stu-id="6ae16-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="6ae16-137">Введите номер телефона, на который будут отправляться текстовые сообщения.</span><span class="sxs-lookup"><span data-stu-id="6ae16-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="6ae16-138">Установите флажок **отправлять меня кода с текстовое сообщение**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-138">Select **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="6ae16-139">Щелкните **контакт мне**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-139">Click **Contact me**.</span></span>
    
6. <span data-ttu-id="6ae16-140">Введите код проверки из текста сообщения, полученного по смарт-телефон и нажмите кнопку **Проверить**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="6ae16-141">На **Шаг 3: сохранение существующих приложений** страницы, запишите пароль отображаемой приложения для учетной записи пользователя 2 в надежном месте и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="6ae16-142">Вернувшись на страницу входа в систему введите пароль для учетной записи пользователя 2 и нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-142">Back on the sign-in page, type the password for the User 2 account and click **Sign in**.</span></span>
    
9. <span data-ttu-id="6ae16-143">Введите код проверки из текста сообщения, полученного по смарт-телефон и нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="6ae16-143">Enter the verification code from the text message received on your smart phone, and then click **Sign in**.</span></span>
    
10. <span data-ttu-id="6ae16-p104">Если это первый раз вы выполнил вход с помощью учетной записи пользователя 2, отображается запрос для изменения пароля. Дважды введите старый пароль и новый пароль и нажмите кнопку **Обновить пароль и выполнить вход**. Запишите новый пароль в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="6ae16-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="6ae16-147">Откроется портал Office 365 для учетной записи User 2.</span><span class="sxs-lookup"><span data-stu-id="6ae16-147">You should see the Office 365 portal for User 2.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="6ae16-148">See Also</span><span class="sxs-lookup"><span data-stu-id="6ae16-148">See Also</span></span>

[<span data-ttu-id="6ae16-149">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="6ae16-149">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="6ae16-150">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="6ae16-150">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="6ae16-151">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="6ae16-151">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="6ae16-152">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="6ae16-152">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="6ae16-153">Планирование для многофакторной проверки подлинности для развертываний Office 365</span><span class="sxs-lookup"><span data-stu-id="6ae16-153">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

