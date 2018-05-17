---
title: Среда разработки и тестирования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: Сводка. Используйте это руководство, чтобы создать пробную подписку Office 365 для оценки или разработки и тестирования.
ms.openlocfilehash: 07922965acfbd23f0f48094fda8b18bf0b66ef38
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="64beb-103">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="64beb-104">**Сводка.** Используйте это руководство, чтобы создать пробную подписку Office 365 для оценки или разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="64beb-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="64beb-p101">Пробную подписку Office 365 можно использовать для создания среды разработки и тестирования для приложений или для демонстрации функций и возможностей Office 365. Существуют две версии:</span><span class="sxs-lookup"><span data-stu-id="64beb-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="64beb-107">Упрощенная среда Office 365 для разработки и тестирования состоит из пробной подписки на Office 365, доступ к которой можно получить с основного компьютера.</span><span class="sxs-lookup"><span data-stu-id="64beb-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="64beb-p102">Используйте эту среду для быстрой демонстрации компонента. Для упрощенной среды разработки и тестирования Office 365 выполните только этапы 2 и 3, описанные в этой статье.</span><span class="sxs-lookup"><span data-stu-id="64beb-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="64beb-p103">Среда Office 365 для разработки и тестирования смоделированного предприятия включает в себя пробную подписку на Office 365 и подключенную к Интернету упрощенную интрасеть организации, которая размещена в службах инфраструктуры Microsoft Azure. Вы можете полностью создать эту конфигурацию в Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="64beb-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="64beb-p104">Эту среду можно использовать для демонстрации функции или приложения в среде, напоминающей обычную сеть организации, подключенную к Интернету, или для функций, которым требуется такой тип среды. Для среды Office 365 для разработки и тестирования смоделированного предприятия выполните этапы 1, 2 и 3 настоящей статьи.</span><span class="sxs-lookup"><span data-stu-id="64beb-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="64beb-p105">Вы можете распечатать эту статью, чтобы записать значения, которые понадобятся вам для этой среды в течение 30 дней пробной подписки на Office 365. Вы легко можете продлить пробную подписку еще на 30 дней. Для постоянной среды тестирования и разработки создайте новую платную подписку с небольшим количеством лицензий.</span><span class="sxs-lookup"><span data-stu-id="64beb-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Руководства по лаборатории тестирования в Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="64beb-118">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="64beb-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="64beb-119">Этап 1. Создание базовой конфигурации в Azure</span><span class="sxs-lookup"><span data-stu-id="64beb-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="64beb-120">Следуйте инструкциям в статье [Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="64beb-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="64beb-p106">Понадобится подписка на Azure. Для этой конфигурации можно использовать [бесплатную пробную подписку](https://azure.microsoft.com/pricing/free-trial/). Если у вас есть подписка на MSDN или Visual Studio, см. страницу [Ежемесячная сумма денег на счете в Azure для подписчиков Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="64beb-p106">You will need an Azure subscription. You can use the [Azure Free Trialhttps://azure.microsoft.com/pricing/free-trial/](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribershttps://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="64beb-124">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="64beb-124">Here is the resulting configuration.</span></span>
  
![Базовая конфигурация среды разработки и тестирования в Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="64beb-126">Эта конфигурация состоит из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="64beb-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="64beb-127">Этап 2. Создание пробной подписки на Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="64beb-128">Чтобы оформить пробную подписку на Office 365 E5, потребуются вымышленное название компании и новая учетная запись Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="64beb-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="64beb-p107">Рекомендуем использовать в качестве названия компании какую-нибудь вариацию имени Contoso (вымышленной компании, используемой в примерах от Майкрософт), но это необязательно. Запишите здесь название своей вымышленной компании: ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="64beb-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn’t required. Record your fictitious company name here: _____________________________________![](./images/Common_Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="64beb-p108">Чтобы зарегистрировать новую учетную запись Майкрософт, перейдите на сайт [https://outlook.com](https://outlook.com) и создайте учетную запись, используя новый адрес электронной почты. Эта учетная запись будет использоваться для регистрации в Office 365.</span><span class="sxs-lookup"><span data-stu-id="64beb-p108">To sign up for a new Microsoft account, go to  https://outlook.com https://outlook.com  and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="64beb-133">Запишите имя и фамилию новой учетной записи здесь: ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="64beb-133">Record the first and last name of your new account here: _______________________________![](./images/Common_Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="64beb-134">Запишите здесь адрес электронной почты новой учетной записи: ![](./images/Common_Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="64beb-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="64beb-135">Оформление пробной подписки на Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="64beb-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="64beb-136">Для создания упрощенной среды разработки и тестирования Office 365 откройте интернет-браузер на компьютере и перейдите на страницу [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="64beb-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to  https://aka.ms/e5trial https://aka.ms/e5trial .</span></span> 
    
    <span data-ttu-id="64beb-137">Для среды разработки и тестирования Office 365, имитирующей предприятие, подключитесь к виртуальной машине CLIENT1 на портале Azure, используя учетную запись CORP\User1.</span><span class="sxs-lookup"><span data-stu-id="64beb-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="64beb-138">На начальном экране запустите Microsoft Edge и перейдите по адресу [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="64beb-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="64beb-139">На странице **приветствия** укажите:</span><span class="sxs-lookup"><span data-stu-id="64beb-139">On the **Welcome, let’s get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="64beb-140">ваше физическое местонахождение;</span><span class="sxs-lookup"><span data-stu-id="64beb-140">Your physical location</span></span>
    
  - <span data-ttu-id="64beb-141">имя и фамилию новой учетной записи Майкрософт;</span><span class="sxs-lookup"><span data-stu-id="64beb-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="64beb-142">новый адрес электронной почты;</span><span class="sxs-lookup"><span data-stu-id="64beb-142">Your new email account address</span></span>
    
  - <span data-ttu-id="64beb-143">рабочий телефон;</span><span class="sxs-lookup"><span data-stu-id="64beb-143">A business phone number</span></span>
    
  - <span data-ttu-id="64beb-144">вымышленное название компании;</span><span class="sxs-lookup"><span data-stu-id="64beb-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="64beb-145">размер организации (250–999 человек).</span><span class="sxs-lookup"><span data-stu-id="64beb-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="64beb-146">Нажмите **Еще одно действие**.</span><span class="sxs-lookup"><span data-stu-id="64beb-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="64beb-147">На странице **создание идентификатора пользователя** введите имя пользователя на основе нового адреса электронной почты, название вымышленной компании после знака @ (удалите все пробелы в названии) и пароль (дважды) для новой учетной записи Office 365. </span><span class="sxs-lookup"><span data-stu-id="64beb-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="64beb-148">Запишите пароль в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="64beb-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="64beb-149">Запишите вымышленное название компании (**название организации**) здесь: ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="64beb-149">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="64beb-150">Нажмите **Создать мою учетную запись**.</span><span class="sxs-lookup"><span data-stu-id="64beb-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="64beb-p109">На странице **Докажите. Что. Вы. Не. Робот.** введите номер телефона, поддерживающего текстовые сообщения, а затем нажмите **Отправить мне SMS**.</span><span class="sxs-lookup"><span data-stu-id="64beb-p109">On the **Prove. You’re. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="64beb-153">Введите код подтверждения из полученного SMS и нажмите **Далее**.</span><span class="sxs-lookup"><span data-stu-id="64beb-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="64beb-154">Запишите здесь URL-адрес страницы входа (выделите и скопируйте): ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="64beb-154">Record the sign-in page URL here (select and copy): ___________________________________________![](./images/Common_Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="64beb-155">Запишите здесь идентификатор пользователя (выделите и скопируйте): ![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="64beb-155">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="64beb-156">Это значение будет называться **именем глобального администратора Office 365**.</span><span class="sxs-lookup"><span data-stu-id="64beb-156">This value will  be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="64beb-157">Когда появится надпись **Все готово к работе**, нажмите ее.</span><span class="sxs-lookup"><span data-stu-id="64beb-157">When you see **You’re ready to go**, click it.</span></span>
    
11. <span data-ttu-id="64beb-158">На следующей странице дождитесь завершения настройки Office 365 и появления всех плиток.</span><span class="sxs-lookup"><span data-stu-id="64beb-158">On the next page, wait until Office 365 completes setting up and all the tiles under Collaborate with Office Online are visible.</span></span>
    
<span data-ttu-id="64beb-159">Появится главная страница портала Office 365, с которой можно получить доступ к службам Office Online и Центру администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="64beb-159">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="64beb-160">Ниже показана итоговая конфигурация для среды разработки и тестирования Office 365, имитирующей предприятие.</span><span class="sxs-lookup"><span data-stu-id="64beb-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Среда разработки и тестирования Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="64beb-162">Конфигурация состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="64beb-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="64beb-163">Виртуальные машины DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="64beb-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="64beb-164">Пробная подписка на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="64beb-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="64beb-165">Этап 3. Настройка пробной подписки на Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="64beb-166">На этом этапе настраивается подписка на Office 365 с дополнительными пользователями и сайтами групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="64beb-166">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="64beb-167">Для начала добавьте четырех новых пользователей и назначьте им лицензии E5.</span><span class="sxs-lookup"><span data-stu-id="64beb-167">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="64beb-168">Следуйте указаниям из статьи [Подключение к Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx), чтобы установить модули PowerShell и подключиться к новой подписке на Office 365 с:</span><span class="sxs-lookup"><span data-stu-id="64beb-168">Use the instructions in [Connect to Office 365 PowerShellhttps://technet.microsoft.com/library/dn975125.aspx](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="64beb-169">компьютера (для упрощенной среды разработки и тестирования Office 365);</span><span class="sxs-lookup"><span data-stu-id="64beb-169">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="64beb-170">виртуальной машины CLIENT1 (для среды Office 365 для разработки и тестирования смоделированного предприятия).</span><span class="sxs-lookup"><span data-stu-id="64beb-170">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="64beb-171">В диалоговом окне "Запрос учетных данных Windows PowerShell" введите имя глобального администратора Office 365 (например, jdoe@contosotoycompany.onmicrosoft.com) и пароль.</span><span class="sxs-lookup"><span data-stu-id="64beb-171">In the Windows PowerShell Credential Request dialog box, type the Office  365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="64beb-172">Введите название организации (например, contosotoycompany) и двузначный код страны, а затем выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="64beb-172">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
> [!TIP]
> <span data-ttu-id="64beb-173">Нажмите [здесь](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34), чтобы скачать текстовый файл, который содержит все команды PowerShell, приведенные в этой статье.</span><span class="sxs-lookup"><span data-stu-id="64beb-173">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all of the PowerShell commands in this article.</span></span>

<span data-ttu-id="64beb-174">Запишите в надежном месте пароль, созданный для пользователя User 2, из вывода команды **New-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="64beb-174">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="64beb-175">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="64beb-175">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="64beb-176">Запишите в надежном месте пароль, созданный для пользователя User 3, из вывода команды **New-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="64beb-176">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="64beb-177">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="64beb-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="64beb-178">Запишите в надежном месте пароль, созданный для пользователя User 4, из вывода команды **New-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="64beb-178">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="64beb-179">Выполните следующие команды в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="64beb-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="64beb-180">Запишите в надежном месте пароль, созданный для пользователя User 5, из вывода команды **New-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="64beb-180">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="64beb-181">Затем создайте три сайта групп SharePoint Online для отделов продаж, производства и поддержки.</span><span class="sxs-lookup"><span data-stu-id="64beb-181">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="64beb-182">Создание трех сайтов групп SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="64beb-182">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="64beb-183">Установите [командную консоль SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251) (версия x64).</span><span class="sxs-lookup"><span data-stu-id="64beb-183">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="64beb-184">Нажмите кнопку **Пуск**, введите **sharepoint** и выберите **Командная консоль SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="64beb-184">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="64beb-185">Введите название организации (например, contosotoycompany), а затем выполните следующие команды в командной консоли SharePoint Online, чтобы подключиться к службе SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="64beb-185">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="64beb-186">В диалоговом окне **Командная консоль Microsoft SharePoint Online** введите имя глобального администратора Office 365 (например, jdoe@contosotoycompany.onmicrosoft.com) и пароль, а затем нажмите кнопку **Войти**.</span><span class="sxs-lookup"><span data-stu-id="64beb-186">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office  365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="64beb-187">Чтобы создать три сайта групп (отделов продаж, производства и поддержки), введите имя глобального администратора Office 365, а затем выполните следующие команды в командной консоли SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="64beb-187">To create three new team sites (Sales, Production, and Support), fill in the Office  365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="64beb-188">Выполните эту команду, чтобы вывести список URL-адресов этих новых сайтов:</span><span class="sxs-lookup"><span data-stu-id="64beb-188">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="64beb-189">Введите в Internet Explorer URL-адрес сайта SharePoint Online для производственного отдела, чтобы просмотреть его.</span><span class="sxs-lookup"><span data-stu-id="64beb-189">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="64beb-190">Запишите значения для дальнейшего использования</span><span class="sxs-lookup"><span data-stu-id="64beb-190">Record values for future reference</span></span>

<span data-ttu-id="64beb-191">Запишите эти значения для использования или развертывания дополнительных руководств в этой тестовой среде:</span><span class="sxs-lookup"><span data-stu-id="64beb-191">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="64beb-192">Имя глобального администратора Office 365: ![](./images/Common_Images/TableLine.png).onmicrosoft.com (с шага 9 этапа 2)</span><span class="sxs-lookup"><span data-stu-id="64beb-192">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="64beb-193">Кроме того, запишите пароль этой учетной записи в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="64beb-193">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="64beb-194">Название организации с пробной подпиской: ![](./images/Common_Images/TableLine.png) (с шага 4 этапа 2)</span><span class="sxs-lookup"><span data-stu-id="64beb-194">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="64beb-195">Чтобы увидеть список учетных записей пользователей User 2, User 3, User 4 и User 5, выполните следующую команду в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="64beb-195">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="64beb-196">Запишите здесь имена учетных записей:</span><span class="sxs-lookup"><span data-stu-id="64beb-196">Record the account names here:</span></span>
    
  - <span data-ttu-id="64beb-197">Имя учетной записи пользователя User 2: user2@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="64beb-197">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="64beb-198">Имя учетной записи пользователя User 3: user3@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="64beb-198">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="64beb-199">Имя учетной записи пользователя User 4: user4@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="64beb-199">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="64beb-200">Имя учетной записи пользователя User 5: user5@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="64beb-200">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="64beb-201">Кроме того, запишите в надежном месте пароли этих учетных записей.</span><span class="sxs-lookup"><span data-stu-id="64beb-201">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="64beb-202">Чтобы увидеть список URL-адресов сайтов групп для отделов продаж, производства и поддержки, выполните следующую команду в командной консоли SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="64beb-202">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="64beb-203">URL-адрес сайта производственного отдела: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="64beb-203">Production site URL:  https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="64beb-204">URL-адрес сайта отдела продаж: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="64beb-204">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="64beb-205">URL-адрес сайта отдела поддержки: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="64beb-205">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="64beb-206">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="64beb-206">Next steps</span></span>

<span data-ttu-id="64beb-207">Используйте следующие статьи в среде разработки и тестирования Office 365:</span><span class="sxs-lookup"><span data-stu-id="64beb-207">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="64beb-208">Синхронизация каталогов для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-208">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-209">Многофакторная проверка подлинности для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-209">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-210">Федеративная идентификация для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-210">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-211">Cloud App Security для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-211">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-212">Advanced Threat Protection для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-212">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-213">Advanced eDiscovery для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-213">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-214">Защита конфиденциальных файлов в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-214">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-215">Изолированный сайт группы SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="64beb-215">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-216">Классификация и маркировка данных в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="64beb-216">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="64beb-217">Добавьте в среду разработки и тестирования Office 365 дополнительные облачные решения Майкрософт:</span><span class="sxs-lookup"><span data-stu-id="64beb-217">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="64beb-218">Среда разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="64beb-218">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="64beb-219">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="64beb-219">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="64beb-220">См. также</span><span class="sxs-lookup"><span data-stu-id="64beb-220">See Also</span></span>

- [<span data-ttu-id="64beb-221">Руководства по лаборатории тестирования для облачных решений</span><span class="sxs-lookup"><span data-stu-id="64beb-221">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="64beb-222">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="64beb-222">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="64beb-223">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="64beb-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


