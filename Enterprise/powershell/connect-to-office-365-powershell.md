---
title: Подключение к Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
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
description: 'Сводка: Подключиться к своей организации Office 365, с помощью Office 365 PowerShell для выполнения задач Центр администрирования из командной строки.'
ms.openlocfilehash: 2ea9c3eaa9a589bed6bf7ac575ffd241b7a72f01
ms.sourcegitcommit: 8cacedcba4627042d4bd17f1a94fddcfd87f77b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2018
ms.locfileid: "25601643"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="f8cd0-103">Подключение к Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8cd0-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="f8cd0-104">**Сводка:** Подключение к организации Office 365 с помощью Office 365 PowerShell для выполнения задач администрирования из командной строки.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="f8cd0-p101">Office 365 PowerShell позволяет Управление параметрами Office 365 с помощью командной строки. Подключение к Office 365 PowerShell — простой процесс, где Установка необходимого программного обеспечения, а затем подключиться к своей организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="f8cd0-107">Существует две версии модуль PowerShell, используемая для подключения к Office 365 и выполнять администрирование учетных записей пользователей, групп и лицензий.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="f8cd0-108">Azure Active Directory PowerShell для диаграммы (включая командлеты **AzureAD** именах)</span><span class="sxs-lookup"><span data-stu-id="f8cd0-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="f8cd0-109">Microsoft Azure модуль Active Directory для Windows PowerShell (включая командлеты **MSol** именах)</span><span class="sxs-lookup"><span data-stu-id="f8cd0-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="f8cd0-p102">По состоянию на дату в этой статье Azure Active Directory PowerShell для модуля график не полностью заменяет функциональные возможности в командлетах модуля Microsoft Azure модуль Active Directory для Windows PowerShell для пользователей, группы и Администрирование лицензирования . Во многих случаях необходимо использовать обеих версий. Безопасно обеих версиях можно установить на том же компьютере.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p102">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="f8cd0-p103">**Никогда не работали с PowerShell?** Посмотрите [этот видеообзор](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) на сайте LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="f8cd0-115">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="f8cd0-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="f8cd0-116">Предполагаемое время выполнения: 5 минут.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="f8cd0-117">Ниже приведены версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="f8cd0-118">Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="f8cd0-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="f8cd0-119">Windows Server 2019 Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 и Windows Server 2008 R2 с пакетом обновления 1</span><span class="sxs-lookup"><span data-stu-id="f8cd0-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="f8cd0-p104">Используйте 64-разрядную версию Windows. Поддержка 32-разрядной версии модуля Microsoft Azure Active Directory для Windows PowerShell прекращена в октябре 2014 г.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="f8cd0-p105">Эти процедуры, предназначены для пользователей, являющихся членами роли администратора Office 365. Дополнительные сведения см в [роли администраторов об Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p105">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f8cd0-124">Связь с Azure Active Directory PowerShell для модуля "график"</span><span class="sxs-lookup"><span data-stu-id="f8cd0-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f8cd0-125">Команды в модуле [Windows Azure Active Directory PowerShell для диаграммы](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) имеют **AzureAD** в имени командлета.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="f8cd0-126">Для процедур, которые требуют новых командлетов в Windows Azure Active Directory PowerShell для модуля "график" используйте следующие действия для установки модуля и подключиться к своей подписке Office 365.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="f8cd0-127">[Windows Azure Active Directory PowerShell для модуля "график"](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) в разделе сведения о поддержке для разных версий Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="f8cd0-128">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="f8cd0-128">Step 1: Install required software</span></span>

<span data-ttu-id="f8cd0-p106">Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="f8cd0-131">Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="f8cd0-132">В командном окне **Администратор: Windows PowerShell** выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f8cd0-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="f8cd0-133">Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="f8cd0-134">Шаг 2: Подключение к Azure AD для подписки Office 365</span><span class="sxs-lookup"><span data-stu-id="f8cd0-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="f8cd0-135">Чтобы подключиться к Azure AD для подписки Office 365 с имя учетной записи и пароль или *многофакторная проверка подлинности (многофакторной проверкой Подлинности)*, выполните следующую команду в командной строке Windows PowerShell (она не обязательно с повышенными привилегиями).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-AzureAD
```

<span data-ttu-id="f8cd0-136">В диалоговом окне **входа в учетную запись** введите работы Office 365 или школа имя учетной записи и пароль и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-136">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="f8cd0-137">При использовании многофакторной проверкой Подлинности следуйте инструкциям в диалоговых окнах дополнительные, чтобы предоставить дополнительные сведения о проверке подлинности, такие как код подтверждения.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-137">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

>[!Tip]
><span data-ttu-id="f8cd0-138">Для подключения к Office 365 Германия видеть [подключение к Германии Azure с помощью PowerShell](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-138">To connect to Office 365 Germany, see [Connect to Azure Germany by using PowerShell](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps).</span></span>
>
    
<span data-ttu-id="f8cd0-139">После подключения, можно использовать новые командлеты для [Windows Azure Active Directory PowerShell для модуля "график"](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-139">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f8cd0-140">Подключение к модулю Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8cd0-140">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f8cd0-141">Имена командлетов в модуле Microsoft Azure Active Directory для Windows PowerShell включают компонент **Msol**.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-141">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="f8cd0-142">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="f8cd0-142">Step 1: Install required software</span></span>

<span data-ttu-id="f8cd0-p107">Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="f8cd0-145">Установите 64-разрядную версию помощника по входу в Microsoft Online Services. См. статью [Помощник по входу в Microsoft Online Services для ИТ-специалистов, RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-145">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="f8cd0-146">Чтобы установить модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="f8cd0-146">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="f8cd0-147">Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-147">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="f8cd0-148">Выполните команду **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-148">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="f8cd0-149">Если отобразится запрос на установку поставщика NuGet, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-149">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="f8cd0-150">Если отобразится запрос на установку модуля из репозитория PSGallery, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-150">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="f8cd0-151">Шаг 2: Подключение к Azure AD для подписки Office 365</span><span class="sxs-lookup"><span data-stu-id="f8cd0-151">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="f8cd0-152">Чтобы подключиться к Azure AD для подписки Office 365 с имя учетной записи и пароль или *многофакторная проверка подлинности (многофакторной проверкой Подлинности)*, выполните следующую команду в командной строке Windows PowerShell (она не обязательно с повышенными привилегиями).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-152">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-MsolService
```

<span data-ttu-id="f8cd0-153">В диалоговом окне **входа в учетную запись** введите работы Office 365 или школа имя учетной записи и пароль и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-153">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="f8cd0-154">При использовании многофакторной проверкой Подлинности следуйте инструкциям в диалоговых окнах дополнительные, чтобы предоставить дополнительные сведения о проверке подлинности, такие как код подтверждения.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-154">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

>[!Tip]
><span data-ttu-id="f8cd0-155">Для подключения к Office 365 Германия видеть [подключение к Германии Azure с помощью PowerShell](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-155">To connect to Office 365 Germany, see [Connect to Azure Germany by using PowerShell](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps).</span></span>
>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="f8cd0-156">Как убедиться, что все получилось?</span><span class="sxs-lookup"><span data-stu-id="f8cd0-156">How do you know this worked?</span></span>

<span data-ttu-id="f8cd0-p108">Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="f8cd0-159">Если возникают ошибки, просмотрите список возможных причин:</span><span class="sxs-lookup"><span data-stu-id="f8cd0-159">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="f8cd0-p109">**Распространенная проблема — неправильный пароль.**. Еще раз выполните шаг 3. Будьте особенно внимательны при вводе имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="f8cd0-p110">\* *Требует Microsoft Azure модуль Active Directory для Windows PowerShell, Microsoft .NET Framework 3.5.* x \* включен на компьютере \**. Вероятно, что на компьютере установлена более новой версии (например, 4 или 4.5.* x \*), но обратной совместимости с предыдущими версиями платформы .NET Framework можно включить или отключить. Дополнительные сведения в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="f8cd0-165">[Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)</span><span class="sxs-lookup"><span data-stu-id="f8cd0-165">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="f8cd0-166">[Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="f8cd0-166">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="f8cd0-167">Windows 10, Windows 8.1 и Windows 8 содержатся в разделе [Установка .NET Framework 3.5 на Windows 10, Windows 8.1 и Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="f8cd0-167">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="f8cd0-p111">**Возможно, используемая вами версия Модуль Microsoft Azure Active Directory для Windows PowerShell устарела.** Чтобы проверить актуальность версии, выполните указанную ниже команду в PowerShell в Office 365 или в Модуль Microsoft Azure Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="f8cd0-170">Если возвращенный номер версии будет меньше 1.0.8070.2, удалите Модуль Microsoft Azure Active Directory для Windows PowerShell и установите последнюю версию, скачав ее по ссылке, указанной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="f8cd0-170">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="f8cd0-171">\*\*Если при подключении возникнет ошибка, ознакомьтесь с \*\*[этой статьей](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="f8cd0-171">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="f8cd0-172">См. также</span><span class="sxs-lookup"><span data-stu-id="f8cd0-172">See also</span></span>

- [<span data-ttu-id="f8cd0-173">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="f8cd0-173">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="f8cd0-174">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8cd0-174">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="f8cd0-175">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8cd0-175">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="f8cd0-176">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="f8cd0-176">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="f8cd0-177">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="f8cd0-177">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

