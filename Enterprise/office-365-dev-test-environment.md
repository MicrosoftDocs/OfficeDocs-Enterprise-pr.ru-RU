---
title: "Среда разработки и тестирования Office 365"
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
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: "Сводка: Используйте руководство в лаборатории тестирования для создания пробную подписку на Office 365 для оценки или разработку и тестирование."
ms.openlocfilehash: 1864043513fc7502ada332ab3b3043ff20a13736
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="00913-103">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="00913-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="00913-104">**Сводка:** В этом документе Test Lab Guide используется для создания пробную подписку на Office 365 для оценки или разработку и тестирование.</span><span class="sxs-lookup"><span data-stu-id="00913-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="00913-p101">Пробную подписку Office 365 можно использовать для создания среды разработки и тестирования для приложений или для демонстрации функций и возможностей Office 365. Существуют две версии:</span><span class="sxs-lookup"><span data-stu-id="00913-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="00913-107">Упрощенная среда Office 365 для разработки и тестирования включает в себя пробную подписку Office 365, доступ к которой можно получить с основного компьютера.</span><span class="sxs-lookup"><span data-stu-id="00913-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="00913-p102">Используйте эту среду для быстрой демонстрации компонента. Для упрощенной среды разработки и тестирования Office 365 выполните этапы 2 и 3, описанные в этой статье.</span><span class="sxs-lookup"><span data-stu-id="00913-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="00913-p103">Среда Office 365 для разработки и тестирования смоделированного предприятия включает в себя пробную подписку на Office 365 и подключенную к Интернету упрощенную интрасеть организации, которая размещена в службах инфраструктуры Microsoft Azure. Вы можете полностью создать эту конфигурацию в Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="00913-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="00913-p104">Эту среду можно использовать для демонстрации функции или приложения в среде, напоминающей обычную сеть организации, подключенную к Интернету, или для функций, которым требуется такой тип среды. Для среды Office 365 для разработки и тестирования смоделированного предприятия выполните этапы 1, 2 и 3 настоящей статьи.</span><span class="sxs-lookup"><span data-stu-id="00913-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="00913-p105">Вы можете распечатать эту статью, чтобы записать значения, которые понадобятся вам для этой среды в течение 30 дней пробной подписки на Office 365. Вы легко можете продлить пробную подписку еще на 30 дней. Для постоянной среды тестирования и разработки создайте новую платную подписку с небольшим количеством лицензий.</span><span class="sxs-lookup"><span data-stu-id="00913-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Руководства по лаборатории тестирования в Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="00913-118">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="00913-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="00913-119">Этап 1. Создание базовой конфигурации в Azure</span><span class="sxs-lookup"><span data-stu-id="00913-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="00913-120">Следуйте инструкциям, представленным в [среде разработки и тестирования базовой конфигурации](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="00913-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="00913-p106">Необходимо будет Azure подписки. [Бесплатная пробная версия Azure](https://azure.microsoft.com/pricing/free-trial/) можно использовать для этой конфигурации. Если у вас есть подписка на MSDN или Visual Studio, видеть [кредит ежемесячный Azure для подписчиков Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="00913-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="00913-124">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="00913-124">Here is the resulting configuration.</span></span>
  
![Базовая конфигурация среды разработки и тестирования в Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="00913-126">Эта конфигурация состоит из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="00913-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="00913-127">Этап 2. Создание пробной подписки на Office 365</span><span class="sxs-lookup"><span data-stu-id="00913-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="00913-128">Чтобы оформить пробную подписку на Office 365 E5, потребуются вымышленное название компании и новая учетная запись Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="00913-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="00913-p107">Рекомендуется использовать значение variant, название компании Contoso для название компании, которая вымышленной компании, используемые в Microsoft образцы контента, но она не требуется. Запишите имя вымышленной компании: ___</span><span class="sxs-lookup"><span data-stu-id="00913-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: _____________________________________</span></span>
    
2. <span data-ttu-id="00913-p108">Чтобы зарегистрировать новую учетную запись Майкрософт, перейдите к [https://outlook.com](https://outlook.com) и создание учетной записи с помощью новой учетной записи электронной почты и адрес. Эта учетная запись будет использоваться для подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="00913-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="00913-133">Запишите имя и фамилию новой учетной записи здесь: _______________________________</span><span class="sxs-lookup"><span data-stu-id="00913-133">Record the first and last name of your new account here: _______________________________</span></span>
    
  - <span data-ttu-id="00913-134">Запишите здесь адрес электронной почты новой учетной записи: _____________________________@outlook.com</span><span class="sxs-lookup"><span data-stu-id="00913-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="00913-135">Оформление пробной подписки на Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="00913-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="00913-136">Упрощенный Office 365 dev/тестовой среды откройте веб-браузер на вашем компьютере и перейдите к [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="00913-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="00913-137">Для имитации enterprise Office 365 dev/тестовой среды:</span><span class="sxs-lookup"><span data-stu-id="00913-137">For the simulated enterprise Office 365 dev/test environment:</span></span>
    
  - <span data-ttu-id="00913-138">С [Azure портала](https://portal.azure.com), подключиться к CLIENT1 с CORP\\учетной записи User1.</span><span class="sxs-lookup"><span data-stu-id="00913-138">From the [Azure portal](https://portal.azure.com), connect to CLIENT1 with the CORP\\User1 account.</span></span>
    
  - <span data-ttu-id="00913-139">Откройте командную строку Windows PowerShell с правами администратора и выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="00913-139">Open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > <span data-ttu-id="00913-140">Щелкните [здесь](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) для получения текстовый файл, содержащий все команды PowerShell в данной статье.</span><span class="sxs-lookup"><span data-stu-id="00913-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
  - <span data-ttu-id="00913-141">На начальном экране выберите пункт **Internet Explorer** и перейдите к [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="00913-141">From the Start screen, click **Internet Explorer** and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="00913-142">На странице **приветствия, давайте рассмотрим знать, можно** укажите:</span><span class="sxs-lookup"><span data-stu-id="00913-142">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="00913-143">ваше физическое местонахождение;</span><span class="sxs-lookup"><span data-stu-id="00913-143">Your physical location</span></span>
    
  - <span data-ttu-id="00913-144">имя и фамилию новой учетной записи Майкрософт;</span><span class="sxs-lookup"><span data-stu-id="00913-144">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="00913-145">новый адрес электронной почты;</span><span class="sxs-lookup"><span data-stu-id="00913-145">Your new email account address</span></span>
    
  - <span data-ttu-id="00913-146">рабочий телефон;</span><span class="sxs-lookup"><span data-stu-id="00913-146">A business phone number</span></span>
    
  - <span data-ttu-id="00913-147">вымышленное название компании;</span><span class="sxs-lookup"><span data-stu-id="00913-147">Your fictional company name</span></span>
    
  - <span data-ttu-id="00913-148">размер организации (250–999 человек).</span><span class="sxs-lookup"><span data-stu-id="00913-148">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="00913-149">Щелкните **только что один этап**.</span><span class="sxs-lookup"><span data-stu-id="00913-149">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="00913-150">На странице **Создание код пользователя** введите имя пользователя, на основании свой новый адрес электронной почты, вымышленной компании после знак @ (удалить все пробелы в имени), а затем пароль (два раза) для этого нового Office 365 учетная запись.</span><span class="sxs-lookup"><span data-stu-id="00913-150">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="00913-151">Запишите пароль в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="00913-151">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="00913-152">Запишите свое имя вымышленной компании, чтобы рассматриваться, как **Название организации**, здесь: ___</span><span class="sxs-lookup"><span data-stu-id="00913-152">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="00913-153">Нажмите кнопку **Создать учетную запись**.</span><span class="sxs-lookup"><span data-stu-id="00913-153">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="00913-p109">На **Подтверждение. Вы. Не. A. робот.** Введите номер телефона, поддерживающим текст телефона и нажмите кнопку **текст мне**.</span><span class="sxs-lookup"><span data-stu-id="00913-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="00913-156">Введите код проверки из текст сообщения и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="00913-156">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="00913-157">Запишите здесь URL-адрес страницы входа (выделите и скопируйте): ___________________________________________</span><span class="sxs-lookup"><span data-stu-id="00913-157">Record the sign-in page URL here (select and copy): ___________________________________________</span></span>
    
9. <span data-ttu-id="00913-158">Запишите здесь идентификатор пользователя (выделите и скопируйте): __________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="00913-158">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="00913-159">Это значение будет рассматриваться, как **имя глобального администратора Office 365**.</span><span class="sxs-lookup"><span data-stu-id="00913-159">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="00913-160">Когда **вы будете готовы перейти**, щелкните его.</span><span class="sxs-lookup"><span data-stu-id="00913-160">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="00913-161">На следующей странице Подождите, пока Office 365 завершает параметр копирование и доступны только Плитка.</span><span class="sxs-lookup"><span data-stu-id="00913-161">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="00913-162">Появится главная страница портала Office 365, с которой можно получить доступ к службам Office Online и Центру администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="00913-162">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="00913-163">Ниже показана итоговая конфигурация для среды Office 365 для разработки и тестирования смоделированного предприятия.</span><span class="sxs-lookup"><span data-stu-id="00913-163">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Среда разработки и тестирования Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="00913-165">Конфигурация состоит из следующих компонентов: </span><span class="sxs-lookup"><span data-stu-id="00913-165">This configuration consists of:</span></span> 
  
- <span data-ttu-id="00913-166">Виртуальные машины DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="00913-166">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="00913-167">Пробная подписка на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="00913-167">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="00913-168">Этап 3. Настройка пробной подписки на Office 365</span><span class="sxs-lookup"><span data-stu-id="00913-168">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="00913-169">На этом этапе настраивается подписка на Office 365 с дополнительными пользователями и сайтами групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="00913-169">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="00913-170">Для начала добавьте четырех новых пользователей и назначьте им лицензии E5.</span><span class="sxs-lookup"><span data-stu-id="00913-170">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="00913-171">Используйте инструкции из статьи Установка модулей PowerShell и подключиться к новой подписки Office 365 через [подключение к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) :</span><span class="sxs-lookup"><span data-stu-id="00913-171">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="00913-172">компьютера (для упрощенной среды разработки и тестирования Office 365);</span><span class="sxs-lookup"><span data-stu-id="00913-172">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="00913-173">виртуальной машины CLIENT1 (для среды Office 365 для разработки и тестирования смоделированного предприятия).</span><span class="sxs-lookup"><span data-stu-id="00913-173">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="00913-174">В диалоговом окне запрос учетных данных Windows PowerShell введите имя глобального администратора Office 365 (пример: jdoe@contosotoycompany.onmicrosoft.com) и пароль.</span><span class="sxs-lookup"><span data-stu-id="00913-174">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="00913-175">Введите название организации (например, contosotoycompany) и двузначный код страны, а затем выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="00913-175">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="00913-176">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи пользователя 2 и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="00913-176">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="00913-177">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="00913-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="00913-178">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи пользователя 3 и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="00913-178">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="00913-179">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="00913-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="00913-180">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи пользователя 4 и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="00913-180">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="00913-181">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="00913-181">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="00913-182">Отображение команду **New-MsolUser** Обратите внимание, созданный пароль для учетной записи пользователя 5 и запишите его в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="00913-182">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="00913-183">Затем создайте три сайта групп SharePoint Online для отделов продаж, производства и поддержки.</span><span class="sxs-lookup"><span data-stu-id="00913-183">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="00913-184">Создание трех сайтов групп SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="00913-184">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="00913-185">Установка [Консоли SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251) (x64 версии).</span><span class="sxs-lookup"><span data-stu-id="00913-185">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="00913-186">Нажмите кнопку **Пуск**, введите **sharepoint**и щелкните **Командная консоль SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="00913-186">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="00913-187">Введите название организации (например, contosotoycompany), а затем выполните следующие команды в командной консоли SharePoint Online, чтобы подключиться к службе SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="00913-187">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="00913-188">В диалоговом окне **Microsoft Командная консоль SharePoint Online** введите имя глобального администратора Office 365 (пример: jdoe@contosotoycompany.onmicrosoft.com) и пароль и нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="00913-188">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="00913-189">Создание трех новых сайтов группы (продаж, производства и поддержки), заполните поля в поле Имя глобального администратора Office 365 и затем выполните следующие команды в командной строке консоли SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="00913-189">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="00913-190">Выполните эту команду, чтобы вывести список URL-адресов этих новых сайтов:</span><span class="sxs-lookup"><span data-stu-id="00913-190">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="00913-191">Введите в Internet Explorer URL-адрес сайта SharePoint Online для производственного отдела, чтобы просмотреть его.</span><span class="sxs-lookup"><span data-stu-id="00913-191">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="00913-192">Запишите значения для дальнейшего использования</span><span class="sxs-lookup"><span data-stu-id="00913-192">Record values for future reference</span></span>

<span data-ttu-id="00913-193">Запишите эти значения для использования или развертывания дополнительных лабораторий тестирования в этой тестовой среде:</span><span class="sxs-lookup"><span data-stu-id="00913-193">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="00913-194">Имя глобального администратора Office 365: ____________________________________.onmicrosoft.com (с шага 9 этапа 2)</span><span class="sxs-lookup"><span data-stu-id="00913-194">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="00913-195">Кроме того, запишите пароль этой учетной записи в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="00913-195">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="00913-196">Название организации с пробной подпиской: _______________________________________________ (с шага 4 этапа 2)</span><span class="sxs-lookup"><span data-stu-id="00913-196">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="00913-197">Чтобы увидеть список учетных записей пользователей User 2, User 3, User 4 и User 5, выполните следующую команду в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="00913-197">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="00913-198">Запишите здесь имена учетных записей:</span><span class="sxs-lookup"><span data-stu-id="00913-198">Record the account names here:</span></span>
    
  - <span data-ttu-id="00913-199">Имя учетно запись пользователя User 2: user2@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="00913-199">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="00913-200">Имя учетно запись пользователя User 3: user3@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="00913-200">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="00913-201">Имя учетно запись пользователя User 4: user4@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="00913-201">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="00913-202">Имя учетно запись пользователя User 5: user5@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="00913-202">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="00913-203">Кроме того, запишите в надежном месте пароли этих учетных записей.</span><span class="sxs-lookup"><span data-stu-id="00913-203">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="00913-204">Чтобы увидеть список URL-адресов сайтов групп для отделов продаж, производства и поддержки, выполните следующую команду в командной консоли SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="00913-204">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="00913-205">URL-адрес сайта рабочей: https://___.sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="00913-205">Production site URL: https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="00913-206">URL-адрес сайта отдела продаж: https://______________________________________________.sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="00913-206">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="00913-207">URL-адрес сайта отдела поддержки: https://______________________________________________.sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="00913-207">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="00913-208">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="00913-208">Next steps</span></span>

<span data-ttu-id="00913-209">Дополнительную информацию о среде разработки и тестирования для Office 365 см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="00913-209">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="00913-210">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="00913-210">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="00913-211">Многофакторная проверка подлинности для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="00913-211">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="00913-212">Федеративное удостоверение для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="00913-212">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="00913-213">Облако безопасности приложения для Office 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="00913-213">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="00913-214">Дополнительные защиту от угроз для вашей среды разработки или тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="00913-214">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="00913-215">Расширенные eDiscovery для вашей среды разработки или тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="00913-215">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="00913-216">Защита конфиденциальных файлов в Office 365 dev/тестовой среде</span><span class="sxs-lookup"><span data-stu-id="00913-216">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="00913-217">Изолированный SharePoint Online группы сайта dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="00913-217">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="00913-218">Классификации данных и маркировки в Office 365 dev/тестовой среде</span><span class="sxs-lookup"><span data-stu-id="00913-218">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="00913-219">Добавьте к среде разработки и тестирования для Office 365 дополнительные облачные решения Майкрософт:</span><span class="sxs-lookup"><span data-stu-id="00913-219">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="00913-220">Microsoft 365 Enterprise dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="00913-220">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="00913-221">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="00913-221">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="00913-222">See Also</span><span class="sxs-lookup"><span data-stu-id="00913-222">See Also</span></span>

[<span data-ttu-id="00913-223">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="00913-223">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="00913-224">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="00913-224">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="00913-225">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="00913-225">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


