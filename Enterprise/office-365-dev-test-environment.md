---
title: Среда разработки и тестирования Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: Сводка. Используйте это руководство, чтобы создать пробную подписку Office 365 для оценки или разработки и тестирования.
ms.openlocfilehash: a49ba10ab9ddded36f21ca9cc92f0482cbe7a4fb
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038036"
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="a3218-103">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="a3218-104">**Сводка.** Используйте это руководство, чтобы создать пробную подписку Office 365 для оценки или разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="a3218-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="a3218-p101">Пробную подписку Office 365 можно использовать для создания среды разработки и тестирования для приложений или для демонстрации функций и возможностей Office 365. Существуют две версии:</span><span class="sxs-lookup"><span data-stu-id="a3218-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="a3218-107">Упрощенная среда Office 365 для разработки и тестирования состоит из пробной подписки на Office 365, доступ к которой можно получить с основного компьютера.</span><span class="sxs-lookup"><span data-stu-id="a3218-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="a3218-p102">Используйте эту среду для быстрой демонстрации компонента. Для упрощенной среды разработки и тестирования Office 365 выполните только этапы 2 и 3, описанные в этой статье.</span><span class="sxs-lookup"><span data-stu-id="a3218-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="a3218-p103">Среда Office 365 для разработки и тестирования смоделированного предприятия включает в себя пробную подписку на Office 365 и подключенную к Интернету упрощенную интрасеть организации, которая размещена в службах инфраструктуры Microsoft Azure. Вы можете полностью создать эту конфигурацию в Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="a3218-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="a3218-p104">Эту среду можно использовать для демонстрации функции или приложения в среде, напоминающей обычную сеть организации, подключенную к Интернету, или для функций, которым требуется такой тип среды. Для среды Office 365 для разработки и тестирования смоделированного предприятия выполните этапы 1, 2 и 3 настоящей статьи.</span><span class="sxs-lookup"><span data-stu-id="a3218-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="a3218-p105">Вы можете распечатать эту статью, чтобы записать значения, которые понадобятся вам для этой среды в течение 30 дней пробной подписки на Office 365. Вы легко можете продлить пробную подписку еще на 30 дней. Для постоянной среды тестирования и разработки создайте новую платную подписку с небольшим количеством лицензий.</span><span class="sxs-lookup"><span data-stu-id="a3218-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Руководства по лаборатории тестирования в Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="a3218-118">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="a3218-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="a3218-119">Этап 1. Создание базовой конфигурации в Azure</span><span class="sxs-lookup"><span data-stu-id="a3218-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="a3218-120">Следуйте инструкциям в статье [Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a3218-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a3218-p106">Понадобится подписка на Azure. Для этой конфигурации можно использовать [бесплатную пробную подписку](https://azure.microsoft.com/pricing/free-trial/). Если у вас есть подписка на MSDN или Visual Studio, см. страницу [Ежемесячная сумма денег на счете в Azure для подписчиков Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="a3218-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="a3218-124">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="a3218-124">Here is the resulting configuration.</span></span>
  
![Базовая конфигурация среды разработки и тестирования в Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
<span data-ttu-id="a3218-126">Эта конфигурация состоит из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="a3218-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="a3218-127">Этап 2. Создание пробной подписки на Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="a3218-128">Чтобы оформить пробную подписку на Office 365 E5, потребуются вымышленное название компании и новая учетная запись Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="a3218-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="a3218-p107">Рекомендуем использовать в качестве названия компании какую-нибудь вариацию имени Contoso (вымышленной компании, используемой в примерах от Майкрософт), но это необязательно. Запишите здесь название своей вымышленной компании: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="a3218-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./media/Common-Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="a3218-p108">Чтобы зарегистрировать новую учетную запись Майкрософт, перейдите на сайт [https://outlook.com](https://outlook.com) и создайте учетную запись, используя новый адрес электронной почты. Эта учетная запись будет использоваться для регистрации в Office 365.</span><span class="sxs-lookup"><span data-stu-id="a3218-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="a3218-133">Запишите имя и фамилию новой учетной записи здесь: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="a3218-133">Record the first and last name of your new account here: ![](./media/Common-Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="a3218-134">Запишите здесь адрес электронной почты новой учетной записи: ![](./media/Common-Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="a3218-134">Record the new email account address here: ![](./media/Common-Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="a3218-135">Оформление пробной подписки на Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="a3218-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="a3218-136">Для создания упрощенной среды разработки и тестирования Office 365 откройте интернет-браузер на компьютере и перейдите на страницу [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="a3218-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="a3218-137">Для среды разработки и тестирования Office 365, имитирующей предприятие, подключитесь к виртуальной машине CLIENT1 на портале Azure, используя учетную запись CORP\User1.</span><span class="sxs-lookup"><span data-stu-id="a3218-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="a3218-138">На начальном экране запустите Microsoft Edge и перейдите по адресу [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="a3218-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="a3218-139">На странице **приветствия** укажите:</span><span class="sxs-lookup"><span data-stu-id="a3218-139">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="a3218-140">ваше физическое местонахождение;</span><span class="sxs-lookup"><span data-stu-id="a3218-140">Your physical location</span></span>
    
  - <span data-ttu-id="a3218-141">имя и фамилию новой учетной записи Майкрософт;</span><span class="sxs-lookup"><span data-stu-id="a3218-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="a3218-142">новый адрес электронной почты;</span><span class="sxs-lookup"><span data-stu-id="a3218-142">Your new email account address</span></span>
    
  - <span data-ttu-id="a3218-143">рабочий телефон;</span><span class="sxs-lookup"><span data-stu-id="a3218-143">A business phone number</span></span>
    
  - <span data-ttu-id="a3218-144">вымышленное название компании;</span><span class="sxs-lookup"><span data-stu-id="a3218-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="a3218-145">размер организации (250–999 человек).</span><span class="sxs-lookup"><span data-stu-id="a3218-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="a3218-146">Нажмите **Еще одно действие**.</span><span class="sxs-lookup"><span data-stu-id="a3218-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="a3218-147">На странице **создание идентификатора пользователя** введите имя пользователя на основе нового адреса электронной почты, название вымышленной компании после знака @ (удалите все пробелы в названии) и пароль (дважды) для новой учетной записи Office 365. </span><span class="sxs-lookup"><span data-stu-id="a3218-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="a3218-148">Запишите пароль в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="a3218-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="a3218-149">Запишите вымышленное название компании (**название организации**) здесь: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="a3218-149">Record your fictional company name, to be referred to as the **organization name**, here: ![](./media/Common-Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="a3218-150">Нажмите **Создать мою учетную запись**.</span><span class="sxs-lookup"><span data-stu-id="a3218-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="a3218-p109">На странице **Докажите. Что. Вы. Не. Робот.** введите номер телефона, поддерживающего текстовые сообщения, а затем нажмите **Отправить мне SMS**.</span><span class="sxs-lookup"><span data-stu-id="a3218-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="a3218-153">Введите код подтверждения из полученного SMS и нажмите **Далее**.</span><span class="sxs-lookup"><span data-stu-id="a3218-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="a3218-154">Запишите здесь URL-адрес страницы входа (выделите и скопируйте): ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="a3218-154">Record the sign-in page URL here (select and copy): ![](./media/Common-Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="a3218-155">Запишите здесь идентификатор пользователя (выделите и скопируйте): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="a3218-155">Record the user ID here (select and copy): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="a3218-156">Это значение будет называться **именем глобального администратора Office 365**.</span><span class="sxs-lookup"><span data-stu-id="a3218-156">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="a3218-157">Когда появится надпись **Все готово к работе**, нажмите ее.</span><span class="sxs-lookup"><span data-stu-id="a3218-157">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="a3218-158">На следующей странице дождитесь завершения настройки Office 365 и появления всех плиток.</span><span class="sxs-lookup"><span data-stu-id="a3218-158">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="a3218-159">Появится главная страница портала Office 365, с которой можно получить доступ к службам Office Online и Центру администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a3218-159">You should see main Office 365 portal page from which you can access Office Online services and the Microsoft 365 Admin center.</span></span>
  
<span data-ttu-id="a3218-160">Ниже показана итоговая конфигурация для среды разработки и тестирования Office 365, имитирующей предприятие.</span><span class="sxs-lookup"><span data-stu-id="a3218-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Среда разработки и тестирования Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="a3218-162">Конфигурация состоит из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="a3218-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="a3218-163">Виртуальные машины DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="a3218-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="a3218-164">Пробная подписка на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="a3218-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="a3218-165">Этап 3. Настройка пробной подписки на Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="a3218-166">На этом этапе настраивается подписка на Office 365 с дополнительными пользователями и им назначаются лицензии Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="a3218-166">In this phase, you configure your Office 365 subscription with additional users and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="a3218-167">Следуйте указаниям из статьи [Подключение к Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module), чтобы подключиться к подписке на Office 365 с модулем PowerShell Azure Active Directory для Graph с:</span><span class="sxs-lookup"><span data-stu-id="a3218-167">Use the instructions in [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) to connect to your Office 365 subscription with the Azure Active Directory PowerShell for Graph module from:</span></span>
  
- <span data-ttu-id="a3218-168">компьютера (для упрощенной среды разработки и тестирования Office 365);</span><span class="sxs-lookup"><span data-stu-id="a3218-168">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="a3218-169">виртуальной машины CLIENT1 (для среды Office 365 для разработки и тестирования смоделированного предприятия).</span><span class="sxs-lookup"><span data-stu-id="a3218-169">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="a3218-170">В диалоговом окне "Запрос учетных данных Windows PowerShell" введите имя глобального администратора Office 365 (например, jdoe@contosotoycompany.onmicrosoft.com) и пароль.</span><span class="sxs-lookup"><span data-stu-id="a3218-170">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="a3218-171">Введите название организации (например, contosotoycompany), двузначный код страны и пароль обычной учетной записи, а затем выполните следующие команды в командной строке PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a3218-171">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a><span data-ttu-id="a3218-172">Этап 4. Создание трех сайтов групп SharePoint Online (необязательно)</span><span class="sxs-lookup"><span data-stu-id="a3218-172">Phase 4: Create three new SharePoint Online team sites (optional)</span></span>

<span data-ttu-id="a3218-173">На этом этапе выполняется настройка набора сайтов групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a3218-173">In this phase, you configure a set of SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="a3218-174">Установите [командную консоль SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251) (версия x64).</span><span class="sxs-lookup"><span data-stu-id="a3218-174">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="a3218-175">Нажмите кнопку **Пуск**, введите **sharepoint** и выберите **Командная консоль SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="a3218-175">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="a3218-176">Введите название организации (например, contosotoycompany), а затем выполните следующие команды в командной консоли SharePoint Online, чтобы подключиться к службе SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="a3218-176">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="a3218-177">В диалоговом окне **Командная консоль Microsoft SharePoint Online** введите имя глобального администратора Office 365 (например, jdoe@contosotoycompany.onmicrosoft.com) и пароль, а затем нажмите кнопку **Войти**.</span><span class="sxs-lookup"><span data-stu-id="a3218-177">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="a3218-178">Чтобы создать три сайта групп (отделов продаж, производства и поддержки), введите имя глобального администратора Office 365, а затем выполните следующие команды в командной консоли SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="a3218-178">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="a3218-179">Выполните эту команду, чтобы вывести список URL-адресов этих новых сайтов:</span><span class="sxs-lookup"><span data-stu-id="a3218-179">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="a3218-180">Введите в Internet Explorer URL-адрес сайта SharePoint Online для производственного отдела, чтобы просмотреть его.</span><span class="sxs-lookup"><span data-stu-id="a3218-180">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="a3218-181">Запишите значения для дальнейшего использования</span><span class="sxs-lookup"><span data-stu-id="a3218-181">Record values for future reference</span></span>

<span data-ttu-id="a3218-182">Запишите эти значения для использования или развертывания дополнительных руководств в этой тестовой среде:</span><span class="sxs-lookup"><span data-stu-id="a3218-182">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="a3218-183">Имя глобального администратора Office 365: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (с шага 9 этапа 2)</span><span class="sxs-lookup"><span data-stu-id="a3218-183">Office 365 global administrator name: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="a3218-184">Кроме того, запишите пароль этой учетной записи в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="a3218-184">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="a3218-185">Название организации с пробной подпиской: ![](./media/Common-Images/TableLine.png) (с шага 4 этапа 2)</span><span class="sxs-lookup"><span data-stu-id="a3218-185">Your trial subscription organization name: ![](./media/Common-Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="a3218-186">Чтобы увидеть список учетных записей пользователей User 2, User 3, User 4 и User 5, выполните следующую команду в командной строке модуля Windows Azure Active Directory для Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a3218-186">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="a3218-187">Запишите здесь имена учетных записей:</span><span class="sxs-lookup"><span data-stu-id="a3218-187">Record the account names here:</span></span>
    
  - <span data-ttu-id="a3218-188">Имя учетной записи пользователя User 2: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="a3218-188">User 2 account name: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="a3218-189">Имя учетной записи пользователя User 3: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="a3218-189">User 3 account name: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="a3218-190">Имя учетной записи пользователя User 4: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="a3218-190">User 4 account name: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="a3218-191">Имя учетной записи пользователя User 5: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="a3218-191">User 5 account name: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="a3218-192">Кроме того, запишите в надежном месте пароли этих учетных записей.</span><span class="sxs-lookup"><span data-stu-id="a3218-192">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="a3218-193">(Необязательно) Чтобы увидеть список URL-адресов сайтов групп для отделов продаж, производства и поддержки, выполните следующую команду в командной консоли SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="a3218-193">(optional) To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="a3218-194">URL-адрес сайта производственного отдела: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="a3218-194">Production site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="a3218-195">URL-адрес сайта отдела продаж: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="a3218-195">Sales site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="a3218-196">URL-адрес сайта отдела поддержки: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="a3218-196">Support site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="a3218-197">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="a3218-197">Next steps</span></span>

<span data-ttu-id="a3218-198">Используйте следующие статьи в среде разработки и тестирования Office 365:</span><span class="sxs-lookup"><span data-stu-id="a3218-198">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="a3218-199">Синхронизация каталогов для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-199">Directory Synchronization for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-200">Многофакторная проверка подлинности для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-200">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-201">Федеративная идентификация для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-201">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-202">Cloud App Security для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-202">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-203">Advanced Threat Protection для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-203">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-204">Advanced eDiscovery для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-204">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-205">Защита конфиденциальных файлов в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-205">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-206">Изолированный сайт группы SharePoint Online в среде разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="a3218-206">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-207">Классификация и маркировка данных в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="a3218-207">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="a3218-208">Добавьте в среду разработки и тестирования Office 365 дополнительные облачные решения Майкрософт:</span><span class="sxs-lookup"><span data-stu-id="a3218-208">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="a3218-209">Среда разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="a3218-209">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="a3218-210">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a3218-210">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="a3218-211">См. также</span><span class="sxs-lookup"><span data-stu-id="a3218-211">See Also</span></span>

- [<span data-ttu-id="a3218-212">Руководства по лаборатории тестирования для облачных решений</span><span class="sxs-lookup"><span data-stu-id="a3218-212">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="a3218-213">Среда разработки и тестирования для Office 365 и Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a3218-213">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="a3218-214">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="a3218-214">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


