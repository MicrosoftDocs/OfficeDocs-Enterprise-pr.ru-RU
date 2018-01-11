---
title: "Подключение к Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: "Сводка. Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки."
ms.openlocfilehash: 942c128d8cfbcf4e78f054a0ab3a51b05173073f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="d5271-103">Подключение к Office 365</span><span class="sxs-lookup"><span data-stu-id="d5271-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="d5271-104">**Сводка.** Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.</span><span class="sxs-lookup"><span data-stu-id="d5271-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="d5271-p101">PowerShell позволяет управлять настройками Office 365 из командной строки. Подключение состоит из трех этапов: установки необходимого программного обеспечения, его запуска и непосредственно подключения к организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="d5271-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="d5271-107">Обратите внимание, что эти инструкции такие же, как в разделе [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span><span class="sxs-lookup"><span data-stu-id="d5271-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="d5271-p102">**Никогда не работали с PowerShell?** Посмотрите [этот видеообзор](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) на сайте LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="d5271-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="d5271-110">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="d5271-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="d5271-111">Предполагаемое время для завершения: 5 минут.</span><span class="sxs-lookup"><span data-stu-id="d5271-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="d5271-112">Ниже приведены версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="d5271-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="d5271-113">Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="d5271-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="d5271-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d5271-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="d5271-p103">Используйте 64-разрядную версию Windows. Поддержка 32-разрядной версии модуля Microsoft Azure Active Directory для Windows PowerShell прекращена в октябре 2014 г.</span><span class="sxs-lookup"><span data-stu-id="d5271-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="d5271-p104">Рабочая или учебная учетная запись Office 365, которая используется для этих процедур, должна иметь права администратора. Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="d5271-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>
    
## <a name="step-1-install-required-software"></a><span data-ttu-id="d5271-119">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="d5271-119">Step 1: Install required software</span></span>

<span data-ttu-id="d5271-p105">Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="d5271-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="d5271-122">Установите 64-разрядную версию [помощника по входу в Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="d5271-122">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="d5271-123">Чтобы установить 64-разрядную версию Модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="d5271-123">Install the 64-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="d5271-124">Откройте веб-страницу [Подключение к Azure Active Directory](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185).</span><span class="sxs-lookup"><span data-stu-id="d5271-124">Open the [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) web page.</span></span>
    
  - <span data-ttu-id="d5271-125">В разделе **Files in Download** (Файлы в пакете) в нижней части страницы нажмите **Download** (Скачать) напротив файла **AdministrationConfig-V1.1.166.0-GA.msi**, а затем установите его.</span><span class="sxs-lookup"><span data-stu-id="d5271-125">In **Files in Download** at the bottom of the page, click **Download** for the **AdministrationConfig-V1.1.166.0-GA.msi** file, and then install it.</span></span>
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a><span data-ttu-id="d5271-126">Шаг 2. Откройте модуль Windows Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="d5271-126">Step 2: Open the Windows Azure Active Directory Module</span></span>

1. <span data-ttu-id="d5271-127">Найдите и откройте Модуль Microsoft Azure Active Directory для Windows PowerShell с помощью одного из указанных ниже методов (в зависимости от используемой версии Windows).</span><span class="sxs-lookup"><span data-stu-id="d5271-127">Find and open the Microsoft Azure Active Directory Module for Windows PowerShell by using one of the following methods based on your version of Windows:</span></span>
    
  - <span data-ttu-id="d5271-128">**Меню "Пуск".** На рабочем столе нажмите **Пуск** и введитеAzure.</span><span class="sxs-lookup"><span data-stu-id="d5271-128">**Start menu** From the desktop, click **Start**, and then type Azure.</span></span>
    
  - <span data-ttu-id="d5271-129">**Без использования меню "Пуск":** выполните поискAzure любым из указанных ниже методов.</span><span class="sxs-lookup"><span data-stu-id="d5271-129">**No Start menu** Search forAzure using any of these methods:</span></span>
    
  - <span data-ttu-id="d5271-130">На начальном экране щелкните пустую область и введите Azure.</span><span class="sxs-lookup"><span data-stu-id="d5271-130">On the Start screen, click an empty area, and type Azure.</span></span>
    
  - <span data-ttu-id="d5271-p106">На рабочем столе или на начальном экране нажмите клавиши Windows+Q. В чудо-кнопке "Поиск" введите Azure.</span><span class="sxs-lookup"><span data-stu-id="d5271-p106">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Azure.</span></span>
    
  - <span data-ttu-id="d5271-p107">На рабочем столе или на начальном экране переместите курсор в правый верхний угол или проведите пальцем влево от правого края экрана, чтобы открыть чудо-кнопки. Выберите чудо-кнопку "Поиск" и введите **Azure**.</span><span class="sxs-lookup"><span data-stu-id="d5271-p107">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and type **Azure**.</span></span>
    
2. <span data-ttu-id="d5271-135">В списке результатов выберите **Модуль Microsoft Azure Active Directory для Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="d5271-135">In the results, click **Microsoft Azure Active Directory Module for Windows PowerShell**.</span></span>
    
## <a name="step-3-connect-to-your-office-365-subscription"></a><span data-ttu-id="d5271-136">Шаг 3. Подключитесь к своей подписке Office 365:</span><span class="sxs-lookup"><span data-stu-id="d5271-136">Step 3: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="d5271-137"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="d5271-137"><a name="step3"> </a></span></span>

<span data-ttu-id="d5271-138">Чтобы использовать только  *имя и пароль учетной записи*  :</span><span class="sxs-lookup"><span data-stu-id="d5271-138">To connect with just an  *account name and password*  :</span></span>
  
1. <span data-ttu-id="d5271-139">В командном окне **Модуль Microsoft Azure Active Directory для Windows PowerShell** выполните следующие команды.</span><span class="sxs-lookup"><span data-stu-id="d5271-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following commands.</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. <span data-ttu-id="d5271-140">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свои имя пользователя и пароль Office 365:рабочая или учебная учетная запись, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d5271-140">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="d5271-141">Чтобы использовать  *многофакторную проверку подлинности (MFA)*  :</span><span class="sxs-lookup"><span data-stu-id="d5271-141">To connect with  *multi-factor authentication (MFA)*  :</span></span>
  
1. <span data-ttu-id="d5271-142">В командном окне **Модуль Microsoft Azure Active Directory для Windows PowerShell** выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="d5271-142">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
  ```
  Connect-MsolService
  ```

2. <span data-ttu-id="d5271-143">В диалоговом окне **Azure Active Directory PowerShell** введите имя пользователя и пароль рабочей или учебной учетной записи Office 365 и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="d5271-143">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
3. <span data-ttu-id="d5271-144">Следуйте инструкциям в диалоговом окне **Azure Active Directory PowerShell**, чтобы указать дополнительные сведения для проверки подлинности, например код подтверждения, и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="d5271-144">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="d5271-145">Как проверить, что все получилось?</span><span class="sxs-lookup"><span data-stu-id="d5271-145">How do you know this worked?</span></span>
<span data-ttu-id="d5271-146"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="d5271-146"><a name="step3"> </a></span></span>

<span data-ttu-id="d5271-p108">Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.</span><span class="sxs-lookup"><span data-stu-id="d5271-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="d5271-149">Если возникают ошибки, просмотрите список возможных причин:</span><span class="sxs-lookup"><span data-stu-id="d5271-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="d5271-p109">**Распространенная проблема  неправильный пароль.**. Еще раз выполните шаг 3. Будьте особенно внимательны при вводе имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="d5271-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="d5271-p110">**Для работы Модуль Microsoft Azure Active Directory для Windows PowerShell необходимо, чтобы на вашем компьютере был включен компонент Платформа Microsoft .NET Framework 3.5. _x_**. Скорее всего, на вашем компьютере будет установлена более новая версия этого компонента (например, 4 или 4.5. _x_), но вы можете включить или отключить режим обратной совместимости с более ранними версиями Платформа .NET Framework. Дополнительные сведения см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="d5271-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="d5271-157">[Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)</span><span class="sxs-lookup"><span data-stu-id="d5271-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="d5271-158">[Установка .NET Framework 3.5 в Windows 8 или Windows 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369) (Windows 8 или Windows 8.1)</span><span class="sxs-lookup"><span data-stu-id="d5271-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="d5271-159">[Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="d5271-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="d5271-p111">**Возможно, используемая вами версия Модуль Microsoft Azure Active Directory для Windows PowerShell устарела.** Чтобы проверить актуальность версии, выполните указанную ниже команду в PowerShell в Office 365 или в Модуль Microsoft Azure Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5271-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="d5271-162">Если возвращенный номер версии будет меньше 1.0.8070.2, удалите Модуль Microsoft Azure Active Directory для Windows PowerShell и установите последнюю версию, скачав ее по ссылке, указанной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="d5271-162">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="d5271-163">**Если при подключении возникнет ошибка, ознакомьтесь с **[этой статьей](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="d5271-163">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="d5271-164">Подключение с помощью модуля Azure Active Directory PowerShell 2</span><span class="sxs-lookup"><span data-stu-id="d5271-164">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="d5271-165"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="d5271-165"><a name="ConnectV2"> </a></span></span>

<span data-ttu-id="d5271-166">Чтобы выполнить действия, требующие использования новых командлетов в [модуле Azure Active Directory PowerShell 2]((https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)), установите его и подключитесь к подписке на Office 365. Вот как это сделать:</span><span class="sxs-lookup"><span data-stu-id="d5271-166">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module]((https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)), use these steps to install the module and connect to your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="d5271-167">Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).</span><span class="sxs-lookup"><span data-stu-id="d5271-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="d5271-168">В командном окне **Администратор: Windows PowerShell** выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="d5271-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="d5271-169">Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="d5271-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>
    
3. <span data-ttu-id="d5271-170">Когда установка нового модуля завершится, используйте эти команды для подключения к подписке на Office 365:</span><span class="sxs-lookup"><span data-stu-id="d5271-170">When the installation of the new module is complete, use these commands to connect to your Office 365 subscription:</span></span>
    
  -  <span data-ttu-id="d5271-171">С помощью *имени учетной записи и пароля*  :</span><span class="sxs-lookup"><span data-stu-id="d5271-171">With an *account name and password*  :</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 <span data-ttu-id="d5271-172">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свои имя пользователя и пароль Office 365:рабочая или учебная учетная запись и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d5271-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
  - <span data-ttu-id="d5271-173">При  *многофакторной проверке подлинности (MFA)*  :</span><span class="sxs-lookup"><span data-stu-id="d5271-173">With  *multi-factor authentication (MFA)*  :</span></span>
    
  ```
  Connect-AzureAD
  ```

<span data-ttu-id="d5271-174">В диалоговом окне **Azure Active Directory PowerShell** введите имя пользователя и пароль рабочей или учебной учетной записи Office 365 и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="d5271-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="d5271-175">Следуйте инструкциям в диалоговом окне **Azure Active Directory PowerShell**, чтобы указать дополнительные сведения для проверки подлинности, например код подтверждения, и нажмите **Войти**.</span><span class="sxs-lookup"><span data-stu-id="d5271-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="d5271-176">После подключения можно использовать новые командлеты для [модуля Azure Active Directory PowerShell 2]((https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)).</span><span class="sxs-lookup"><span data-stu-id="d5271-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module]((https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d5271-177">См. также</span><span class="sxs-lookup"><span data-stu-id="d5271-177">See also</span></span>

#### 

[<span data-ttu-id="d5271-178">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="d5271-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d5271-179">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5271-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="d5271-180">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5271-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[<span data-ttu-id="d5271-181">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="d5271-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="d5271-182">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="d5271-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

