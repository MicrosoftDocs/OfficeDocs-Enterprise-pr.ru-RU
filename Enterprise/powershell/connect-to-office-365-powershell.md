---
title: Подключение к Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Сводка. Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.
ms.openlocfilehash: 71b8c8d61a914fa7fd036fadb7e17ca3f66cd639
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="c84a2-103">Подключение к Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c84a2-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="c84a2-104">**Сводка.** Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.</span><span class="sxs-lookup"><span data-stu-id="c84a2-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="c84a2-p101">PowerShell позволяет управлять настройками Office 365 из командной строки. Подключение состоит из трех этапов: установки необходимого программного обеспечения, его запуска и непосредственно подключения к организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="c84a2-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="c84a2-p102">**Никогда не работали с PowerShell?** Посмотрите [этот видеообзор](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) на сайте LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="c84a2-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c84a2-109">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="c84a2-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="c84a2-110">Предполагаемое время для завершения: 5 минут.</span><span class="sxs-lookup"><span data-stu-id="c84a2-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="c84a2-111">Ниже приведены версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="c84a2-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="c84a2-112">Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="c84a2-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="c84a2-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="c84a2-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="c84a2-p103">Используйте 64-разрядную версию Windows. Поддержка 32-разрядной версии модуля Microsoft Azure Active Directory для Windows PowerShell прекращена в октябре 2014 г.</span><span class="sxs-lookup"><span data-stu-id="c84a2-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="c84a2-p104">Эти процедуры, предназначены для пользователей, являющихся членами роли администратора Office 365. Дополнительные сведения см в [роли администраторов об Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="c84a2-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c84a2-118">Подключение к модулю Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c84a2-118">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c84a2-119">Имена командлетов в модуле Microsoft Azure Active Directory для Windows PowerShell включают компонент **Msol**.</span><span class="sxs-lookup"><span data-stu-id="c84a2-119">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="c84a2-120">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="c84a2-120">Step 1: Install required software</span></span>

<span data-ttu-id="c84a2-p105">Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="c84a2-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="c84a2-123">Установите 64-разрядную версию помощника по входу в Microsoft Online Services. См. статью [Помощник по входу в Microsoft Online Services для ИТ-специалистов, RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="c84a2-123">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="c84a2-124">Чтобы установить модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="c84a2-124">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="c84a2-125">Откройте командную строку для уровня администратора PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c84a2-125">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="c84a2-126">Выполните команду **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="c84a2-126">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="c84a2-127">Если отобразится запрос на установку поставщика NuGet, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="c84a2-127">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="c84a2-128">Если отобразится запрос на установку модуля из репозитория PSGallery, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="c84a2-128">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="c84a2-129">После установки закройте командное окно PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c84a2-129">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-your-office-365-subscription"></a><span data-ttu-id="c84a2-130">Шаг 2. Подключитесь к своей подписке Office 365</span><span class="sxs-lookup"><span data-stu-id="c84a2-130">Step 2: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="c84a2-131"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="c84a2-131"></span></span>

<span data-ttu-id="c84a2-132">Чтобы при подключении использовать только *имя и пароль учетной записи*:</span><span class="sxs-lookup"><span data-stu-id="c84a2-132">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="c84a2-133">Запустите командную строку Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c84a2-133">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="c84a2-134">В командном окне **Windows PowerShell** выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="c84a2-134">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="c84a2-135">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свои имя пользователя и пароль Office 365:рабочая или учебная учетная запись и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="c84a2-135">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="c84a2-136">Чтобы использовать *многофакторную проверку подлинности (MFA)*:</span><span class="sxs-lookup"><span data-stu-id="c84a2-136">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="c84a2-137">Запустите командную строку Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c84a2-137">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="c84a2-138">В командном окне **Модуль Microsoft Azure Active Directory для Windows PowerShell** выполните вот какую команду.</span><span class="sxs-lookup"><span data-stu-id="c84a2-138">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="c84a2-139">В диалоговом окне **Azure Active Directory PowerShell** введите имя пользователя и пароль рабочей или учебной учетной записи Office 365 и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="c84a2-139">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="c84a2-140">Следуйте инструкциям в диалоговом окне **Azure Active Directory PowerShell**, чтобы указать дополнительные сведения для проверки подлинности, например код подтверждения, и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="c84a2-140">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="c84a2-141">Как проверить, что все получилось?</span><span class="sxs-lookup"><span data-stu-id="c84a2-141">How do you know this worked?</span></span>
<span data-ttu-id="c84a2-142"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="c84a2-142"></span></span>

<span data-ttu-id="c84a2-p106">Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.</span><span class="sxs-lookup"><span data-stu-id="c84a2-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="c84a2-145">Если возникают ошибки, просмотрите список возможных причин:</span><span class="sxs-lookup"><span data-stu-id="c84a2-145">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="c84a2-p107">**Распространенная проблема — неправильный пароль.**. Еще раз выполните шаг 3. Будьте особенно внимательны при вводе имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="c84a2-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="c84a2-p108">* *Требует Microsoft Azure модуль Active Directory для Windows PowerShell, Microsoft .NET Framework 3.5.* x * включен на компьютере **. Вероятно, что на компьютере установлена более новой версии (например, 4 или 4.5.* x *), но обратной совместимости с предыдущими версиями платформы .NET Framework можно включить или отключить. Дополнительные сведения в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="c84a2-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.*x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.*x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="c84a2-151">[Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)</span><span class="sxs-lookup"><span data-stu-id="c84a2-151">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="c84a2-152">[Установка .NET Framework 3.5 в Windows 8 или Windows 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369) (Windows 8 или Windows 8.1)</span><span class="sxs-lookup"><span data-stu-id="c84a2-152">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="c84a2-153">[Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="c84a2-153">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="c84a2-p109">**Возможно, используемая вами версия Модуль Microsoft Azure Active Directory для Windows PowerShell устарела.** Чтобы проверить актуальность версии, выполните указанную ниже команду в PowerShell в Office 365 или в Модуль Microsoft Azure Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c84a2-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="c84a2-156">Если возвращенный номер версии будет меньше 1.0.8070.2, удалите Модуль Microsoft Azure Active Directory для Windows PowerShell и установите последнюю версию, скачав ее по ссылке, указанной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="c84a2-156">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="c84a2-157">**Если при подключении возникнет ошибка, ознакомьтесь с **[этой статьей](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="c84a2-157">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c84a2-158">Связь с Azure Active Directory PowerShell для модуля "график"</span><span class="sxs-lookup"><span data-stu-id="c84a2-158">Connect with the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="c84a2-159"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="c84a2-159"></span></span>

<span data-ttu-id="c84a2-160">Команды в Azure Active Directory PowerShell для модуля графике иметь «AzureAD» в имени командлета.</span><span class="sxs-lookup"><span data-stu-id="c84a2-160">Commands in the Azure Active Directory PowerShell for Graph module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="c84a2-161">Для процедур, которые требуют новых командлетов в Windows Azure Active Directory PowerShell для модуля "график" используйте следующие действия для установки модуля и подключиться к своей подписке Office 365.</span><span class="sxs-lookup"><span data-stu-id="c84a2-161">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="c84a2-162">[Windows Azure Active Directory PowerShell для модуля "график"](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) в разделе сведения о поддержке для разных версий Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="c84a2-162">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="c84a2-163">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="c84a2-163">Step 1: Install required software</span></span>

<span data-ttu-id="c84a2-p110">Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="c84a2-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="c84a2-166">Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).</span><span class="sxs-lookup"><span data-stu-id="c84a2-166">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="c84a2-167">В командном окне **Администратор: Windows PowerShell** выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c84a2-167">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="c84a2-168">Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="c84a2-168">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-office-365"></a><span data-ttu-id="c84a2-169">Шаг 2. Подключитесь к Office 365</span><span class="sxs-lookup"><span data-stu-id="c84a2-169">Step 2: Connect to Office 365</span></span>

<span data-ttu-id="c84a2-170">Чтобы подключиться к подписке на Office 365 с помощью *имени и пароля учетной записи*:</span><span class="sxs-lookup"><span data-stu-id="c84a2-170">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="c84a2-171">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свои имя пользователя и пароль Office 365:рабочая или учебная учетная запись и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="c84a2-171">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="c84a2-172">Чтобы подключиться к подписке на Office 365 с использованием *многофакторной проверки подлинности (MFA)*:</span><span class="sxs-lookup"><span data-stu-id="c84a2-172">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="c84a2-173">В диалоговом окне **Azure Active Directory PowerShell** введите имя пользователя и пароль рабочей или учебной учетной записи Office 365 и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="c84a2-173">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="c84a2-174">Следуйте инструкциям в диалоговом окне **Azure Active Directory PowerShell**, чтобы указать дополнительные сведения для проверки подлинности, например код подтверждения, и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="c84a2-174">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="c84a2-175">После подключения, можно использовать новые командлеты для [Windows Azure Active Directory PowerShell для модуля "график"](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="c84a2-175">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c84a2-176">См. также</span><span class="sxs-lookup"><span data-stu-id="c84a2-176">See also</span></span>

- [<span data-ttu-id="c84a2-177">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="c84a2-177">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="c84a2-178">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c84a2-178">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="c84a2-179">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c84a2-179">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="c84a2-180">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c84a2-180">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="c84a2-181">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="c84a2-181">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

