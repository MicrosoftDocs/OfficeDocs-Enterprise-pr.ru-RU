---
title: Многофакторная проверка подлинности для среды разработки и тестирования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: Сводка. Настройка многофакторной проверки подлинности с помощью текстовых сообщений, отправляемых на смартфон, в среде разработки и тестирования Office 365.
ms.openlocfilehash: 453dbc6bda3cfbc6806159d53c9a805c4c6cac97
ms.sourcegitcommit: 8e2760cbcaf564923595147ccf6da468edaed364
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2019
ms.locfileid: "30242081"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="7bc23-103">Многофакторная проверка подлинности для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="7bc23-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="7bc23-104">**Сводка.** Настройка многофакторной проверки подлинности с помощью текстовых сообщений, отправляемых на смартфон, в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="7bc23-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="7bc23-p101">Для дополнительного уровня безопасности при входе в вашу подписку на Office 365 вы можете включить многофакторную проверку подлинности Azure, которая требует больше, чем просто имя пользователя и пароль для проверки подлинности учетной записи. При использовании многофакторной проверки подлинности для Office 365 пользователям необходимо подтвердить телефонный звонок, ввести код проверки, отправленный в текстовом сообщении, или указать пароль приложения на смарт-телефонах после правильного ввода пароля. Они могут войти только после того, как будет удовлетворен второй фактор проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="7bc23-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="7bc23-108">В этой статье описано, как включить проверку подлинности на основе текстовых сообщений для учетной записи Office 365 и проверить ее работу.</span><span class="sxs-lookup"><span data-stu-id="7bc23-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="7bc23-109">Настройка многофакторной проверки подлинности для Office 365 в среде разработки и тестирования состоит из двух этапов:</span><span class="sxs-lookup"><span data-stu-id="7bc23-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="7bc23-110">Создание среды разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="7bc23-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="7bc23-111">Включение и проверка многофакторной проверки подлинности для учетной записи User 2.</span><span class="sxs-lookup"><span data-stu-id="7bc23-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="7bc23-112">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="7bc23-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="7bc23-113">Этап 1. Создание среды разработки и тестирования Office 365 — упрощенной или для имитированных предприятий</span><span class="sxs-lookup"><span data-stu-id="7bc23-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="7bc23-114">Если вы только хотите протестировать многофакторную проверку подлинности в упрощенном виде с минимальными требованиями, следуйте инструкциям в статье 2 и 3 of a [Office 365 dev/test Environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="7bc23-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="7bc23-115">Если вы хотите протестировать многофакторную проверку подлинности на имитации предприятия, следуйте инструкциям в статье [DirSync для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="7bc23-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="7bc23-p102">Для проверки не требуется условная корпоративная среда разработки и тестирования, которая включает условную интрасеть, подключенную к Интернету, и синхронизацию каталогов для леса Windows Server AD. Она показана здесь лишь для того, чтобы вы могли проверить многофакторную проверку подлинности и поэкспериментировать с этим компонентом в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="7bc23-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="7bc23-118">Этап 2. Включение и проверка многофакторной проверки подлинности для учетной записи User 2</span><span class="sxs-lookup"><span data-stu-id="7bc23-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="7bc23-119">Чтобы включить многофакторную проверку подлинности для учетной записи User 2, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="7bc23-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="7bc23-120">Откройте отдельный экземпляр браузера, перейдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)), а затем войдите в пробную подПиску на Office 365 с помощью учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="7bc23-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="7bc23-121">На главной странице портала нажмите **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="7bc23-122">На панели навигации слева выберите **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="7bc23-123">В области активные пользователи щелкните **Дополнительные настройки многофакторной проверки подлиннОсти _гт_**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-123">In the Active users pane, click **More > Multi-factor authentication setup**.</span></span>
    
5. <span data-ttu-id="7bc23-124">В списке выберите учетную запись **пользователя 2** .</span><span class="sxs-lookup"><span data-stu-id="7bc23-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="7bc23-125">В разделе **пользователь 2** в разделе **быстрые действия**нажмите кнопку **включить**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="7bc23-126">В диалоговом окне **Сведения о включении многофакторной проверки подлинности** нажмите **Включить проверку Multi-Factor Auth**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="7bc23-127">В диалоговом окне **успешное обновление** нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-127">In the **Updates successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="7bc23-128">На вкладке **Домашняя страница Microsoft Office** щелкните значок учетной записи пользователя в правом верхнем углу и нажмите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="7bc23-129">Закройте окно браузера.</span><span class="sxs-lookup"><span data-stu-id="7bc23-129">Close your browser instance.</span></span>
    
<span data-ttu-id="7bc23-130">Чтобы настроить отправку текстового сообщения для проверки учетной записи User 2 и проверить ее, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="7bc23-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="7bc23-131">Откройте новое окно браузера.</span><span class="sxs-lookup"><span data-stu-id="7bc23-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="7bc23-132">Перейдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)) и войдите в систему с учетной записью пользователя 2 (\<Пользователь2 @ Organization наме_гт_. onmicrosoft. com) и паролем.</span><span class="sxs-lookup"><span data-stu-id="7bc23-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="7bc23-p103">После входа вам будет предложено настроить дополнительную проверку безопасности для учетной записи. Нажмите **Настроить сейчас**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="7bc23-135">На странице **Дополнительная проверка безопасности**: </span><span class="sxs-lookup"><span data-stu-id="7bc23-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="7bc23-136">Выберите свою страну или регион.</span><span class="sxs-lookup"><span data-stu-id="7bc23-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="7bc23-137">Введите номер телефона, на который будут отправляться текстовые сообщения.</span><span class="sxs-lookup"><span data-stu-id="7bc23-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="7bc23-138">в поле **метод**нажмите кнопку **отправить код по текстовому сообщению**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="7bc23-139">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="7bc23-140">Введите код проверки из текстового сообщения, полученного на смартфон, и нажмите **Проверить**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="7bc23-141">На странице **Шаг 3. Продолжайте использовать имеющиеся приложения** скопируйте отображаемый пароль приложения для учетной записи User 2 в надежное место и нажмите **Готово**.</span><span class="sxs-lookup"><span data-stu-id="7bc23-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="7bc23-p104">При первом входе в учетную запись User 2 вам будет предложено изменить пароль. Введите исходный пароль и новый пароль дважды и нажмите **Обновить пароль и войти**. Запишите новый пароль в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="7bc23-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="7bc23-145">На вкладке **домашнЯя страница Microsoft Office** в браузере должен появиться портал Office 365 для пользователя 2.</span><span class="sxs-lookup"><span data-stu-id="7bc23-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="7bc23-146">См. также</span><span class="sxs-lookup"><span data-stu-id="7bc23-146">See Also</span></span>

[<span data-ttu-id="7bc23-147">Руководства по созданию сред разработки и тестирования облачных решений</span><span class="sxs-lookup"><span data-stu-id="7bc23-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="7bc23-148">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="7bc23-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="7bc23-149">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="7bc23-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="7bc23-150">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="7bc23-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="7bc23-151">Планирование многофакторной проверки подлинности для развертываний Office 365</span><span class="sxs-lookup"><span data-stu-id="7bc23-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

