---
title: Подключение к Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Сводка. Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.
ms.openlocfilehash: aea7cb638cb866374af6b33d6d1848a7cb6d304c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069095"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="63d4a-103">Подключение к Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="63d4a-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="63d4a-104">**Сводка.** Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.</span><span class="sxs-lookup"><span data-stu-id="63d4a-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="63d4a-105">PowerShell в Office 365 позволяет управлять параметрами Office 365 из командной строки.</span><span class="sxs-lookup"><span data-stu-id="63d4a-105">Office 365 PowerShell lets you to manage your Office 365 admin center settings from the command line.</span></span> <span data-ttu-id="63d4a-106">Подключение к PowerShell в Office 365 — это простой процесс установки необходимого программного обеспечения и последующего подключения к организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="63d4a-106">Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="63d4a-107">Существует две версии модуля PowerShell, которые используются для подключения к Office 365 и управления учетными записями пользователей, группами и лицензиями:</span><span class="sxs-lookup"><span data-stu-id="63d4a-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="63d4a-108">Azure Active Directory PowerShell для Graph (командлеты содержат **AzureAD** в своем имени)</span><span class="sxs-lookup"><span data-stu-id="63d4a-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="63d4a-109">Модуль Microsoft Azure Active Directory для Windows PowerShell (командлеты содержат **MSol** в своем имени)</span><span class="sxs-lookup"><span data-stu-id="63d4a-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="63d4a-110">На момент выхода этой статьи модуль Azure Active Directory PowerShell для Graph не полностью заменяет функции командлетов модуля Microsoft Azure Active Directory для Windows PowerShell при администрировании пользователей, групп и лицензий.</span><span class="sxs-lookup"><span data-stu-id="63d4a-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="63d4a-111">Во многих случаях необходимо использовать обе версии.</span><span class="sxs-lookup"><span data-stu-id="63d4a-111">In many cases, you need to use both versions.</span></span> <span data-ttu-id="63d4a-112">Вы можете безопасно установить обе версии на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="63d4a-112">You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="63d4a-p103">
  \*\*Никогда не работали с PowerShell?\*\* Посмотрите [этот видеообзор](https://support.office.com/ru-RU/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) на сайте LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="63d4a-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="63d4a-115">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="63d4a-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="63d4a-116">Предполагаемое время для завершения: 5 минут.</span><span class="sxs-lookup"><span data-stu-id="63d4a-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="63d4a-117">Ниже приведены версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="63d4a-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="63d4a-118">Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="63d4a-118">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="63d4a-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="63d4a-119">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="63d4a-p104">Используйте 64-разрядную версию Windows. Поддержка 32-разрядной версии модуля Microsoft Azure Active Directory для Windows PowerShell прекращена в октябре 2014 г.</span><span class="sxs-lookup"><span data-stu-id="63d4a-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="63d4a-122">Эти процедуры предназначены для пользователей, являющихся участниками роли администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="63d4a-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="63d4a-123">Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="63d4a-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="63d4a-124">Подключение к модулю Azure Active Directory PowerShell для Graph</span><span class="sxs-lookup"><span data-stu-id="63d4a-124">Next, you Connect with the Azure Active Directory PowerShell for Graph module .</span></span>

<span data-ttu-id="63d4a-125">Имена командлетов в модуле [Azure Active Directory PowerShell для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) включают компонент **AzureAD**.</span><span class="sxs-lookup"><span data-stu-id="63d4a-125">Commands in the Azure Active Directory V2 PowerShell module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="63d4a-126">Чтобы выполнить действия, требующие использования новых командлетов в модуле Azure Active Directory PowerShell для Graph, установите его и подключитесь к подписке на Office 365. Вот как это сделать:</span><span class="sxs-lookup"><span data-stu-id="63d4a-126">For procedures that require the new cmdlets in the Azure Active Directory V2 PowerShell module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="63d4a-127">Информацию о поддержке в различных версиях Microsoft Windows см. в [этой статье](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="63d4a-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="63d4a-128">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="63d4a-128">Step 1: Install required software</span></span>

<span data-ttu-id="63d4a-p106">Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="63d4a-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="63d4a-131">Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).</span><span class="sxs-lookup"><span data-stu-id="63d4a-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="63d4a-132">В командном окне **Администратор: Windows PowerShell** выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="63d4a-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="63d4a-133">Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="63d4a-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="63d4a-134">Шаг 2. Подключитесь к Azure AD для своей подписки Office 365</span><span class="sxs-lookup"><span data-stu-id="63d4a-134">Step 2: Connect to your Office 365 subscription</span></span>

<span data-ttu-id="63d4a-135">Чтобы подключиться к Azure AD для своей подписки на Office 365 с помощью имени учетной записи и пароля или с помощью *многофакторной проверкой подлинности (MFA)*, запустите одну из этих команд в командной строке Windows PowerShell (повышенные привилегии не требуются).</span><span class="sxs-lookup"><span data-stu-id="63d4a-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="63d4a-136">**Облачная служба Office 365**</span><span class="sxs-lookup"><span data-stu-id="63d4a-136">**Office 365 cloud**</span></span> | <span data-ttu-id="63d4a-137">**Команда**</span><span class="sxs-lookup"><span data-stu-id="63d4a-137">**Command**</span></span> |
| <span data-ttu-id="63d4a-138">Office 365 Worldwide (+GCC)</span><span class="sxs-lookup"><span data-stu-id="63d4a-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="63d4a-139">Office 365, предоставляемый 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="63d4a-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="63d4a-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="63d4a-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="63d4a-141">Office 365 для DoD государственных организаций США и Office 365 для GCC High государственных организаций США</span><span class="sxs-lookup"><span data-stu-id="63d4a-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="63d4a-142">В диалоговом окне **Вход в учетную запись** введите имя пользователя и пароль своей рабочей или учебной учетной записи Office 365 и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="63d4a-142">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="63d4a-143">Если вы используете многофакторную проверку подлинности, следуйте инструкциям в дополнительных диалоговых окнах, чтобы предоставить дополнительные сведения для проверки подлинности, например код проверки.</span><span class="sxs-lookup"><span data-stu-id="63d4a-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="63d4a-144">После подключения можно использовать новые командлеты для [модуля Azure Active Directory PowerShell для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="63d4a-144">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="63d4a-145">Подключение к модулю Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="63d4a-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="63d4a-146">Имена командлетов в модуле Microsoft Azure Active Directory для Windows PowerShell включают компонент **Msol**.</span><span class="sxs-lookup"><span data-stu-id="63d4a-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="63d4a-147">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="63d4a-147">Step 1: Install required software</span></span>

<span data-ttu-id="63d4a-p107">Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="63d4a-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="63d4a-150">Установите 64-разрядную версию помощника по входу в Microsoft Online Services. См. статью [Помощник по входу в Microsoft Online Services для ИТ-специалистов, RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="63d4a-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="63d4a-151">Чтобы установить модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="63d4a-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="63d4a-152">Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).</span><span class="sxs-lookup"><span data-stu-id="63d4a-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="63d4a-153">Выполните команду **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="63d4a-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="63d4a-154">Если отобразится запрос на установку поставщика NuGet, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="63d4a-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="63d4a-155">Если отобразится запрос на установку модуля из репозитория PSGallery, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="63d4a-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="63d4a-156">Шаг 2. Подключитесь к Azure AD для своей подписки Office 365</span><span class="sxs-lookup"><span data-stu-id="63d4a-156">Step 2: Connect to your Office 365 subscription</span></span>

<span data-ttu-id="63d4a-157">Чтобы подключиться к Azure AD для своей подписки на Office 365 с помощью имени учетной записи и пароля или с помощью *многофакторной проверкой подлинности (MFA)*, запустите одну из этих команд в командной строке Windows PowerShell (повышенные привилегии не требуются).</span><span class="sxs-lookup"><span data-stu-id="63d4a-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="63d4a-158">**Облачная служба Office 365**</span><span class="sxs-lookup"><span data-stu-id="63d4a-158">**Office 365 cloud**</span></span> | <span data-ttu-id="63d4a-159">**Команда**</span><span class="sxs-lookup"><span data-stu-id="63d4a-159">**Command**</span></span> |
| <span data-ttu-id="63d4a-160">Office 365 Worldwide (+GCC)</span><span class="sxs-lookup"><span data-stu-id="63d4a-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="63d4a-161">Office 365, предоставляемый 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="63d4a-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="63d4a-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="63d4a-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="63d4a-163">Office 365 для DoD государственных организаций США и Office 365 для GCC High государственных организаций США</span><span class="sxs-lookup"><span data-stu-id="63d4a-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="63d4a-164">В диалоговом окне **Вход в учетную запись** введите имя пользователя и пароль своей рабочей или учебной учетной записи Office 365 и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="63d4a-164">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="63d4a-165">Если вы используете многофакторную проверку подлинности, следуйте инструкциям в дополнительных диалоговых окнах, чтобы предоставить дополнительные сведения для проверки подлинности, например код проверки.</span><span class="sxs-lookup"><span data-stu-id="63d4a-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="63d4a-166">Как проверить, все ли получилось?</span><span class="sxs-lookup"><span data-stu-id="63d4a-166">How do you know this worked?</span></span>

<span data-ttu-id="63d4a-p108">Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.</span><span class="sxs-lookup"><span data-stu-id="63d4a-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="63d4a-169">Если возникают ошибки, просмотрите список возможных причин ниже.</span><span class="sxs-lookup"><span data-stu-id="63d4a-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="63d4a-170">**Распространенная проблема  неправильный пароль.**.</span><span class="sxs-lookup"><span data-stu-id="63d4a-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="63d4a-171">Еще раз выполните шаг 2,</span><span class="sxs-lookup"><span data-stu-id="63d4a-171">Run Step 3 again.</span></span> <span data-ttu-id="63d4a-172">внимательно проверив вводимое имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="63d4a-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="63d4a-173">**Для работы модуля Microsoft Azure Active Directory для Windows PowerShell необходимо, чтобы на вашем компьютере был включен компонент Microsoft .NET Framework 3.5.* x*. Скорее всего, на вашем компьютере установлена более новая версия этого компонента (например, 4 или 4.5.\* x\*), но вы можете включить или отключить режим обратной совместимости с более ранними версиями платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63d4a-173">The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. x feature is enabled on your computer. It's likely that your computer has a newer version installed (for example, 4 or 4.5. x), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span> <span data-ttu-id="63d4a-174">Дополнительную информацию см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="63d4a-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="63d4a-175">[Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)</span><span class="sxs-lookup"><span data-stu-id="63d4a-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="63d4a-176">[Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="63d4a-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="63d4a-177">
  [Установка платформы .NET Framework 3.5 на Windows 10, Windows 8.1 и Windows 8](https://docs.microsoft.com/ru-RU/dotnet/framework/install/dotnet-35-windows-10) (Windows 10, Windows 8.1 и Windows 8)</span><span class="sxs-lookup"><span data-stu-id="63d4a-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="63d4a-p111">**Возможно, используемая вами версия Модуль Microsoft Azure Active Directory для Windows PowerShell устарела.** Чтобы проверить актуальность версии, выполните указанную ниже команду в PowerShell в Office 365 или в Модуль Microsoft Azure Active Directory для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63d4a-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="63d4a-180">Если возвращенный номер версии будет меньше 1.0.8070.2, удалите Модуль Microsoft Azure Active Directory для Windows PowerShell и установите последнюю версию, скачав ее по ссылке, указанной на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="63d4a-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="63d4a-181">\*\*Если при подключении возникнет ошибка, ознакомьтесь с \*\*[этой статьей](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="63d4a-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="63d4a-182">См. также</span><span class="sxs-lookup"><span data-stu-id="63d4a-182">See also</span></span>

- [<span data-ttu-id="63d4a-183">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="63d4a-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="63d4a-184">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="63d4a-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="63d4a-185">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="63d4a-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="63d4a-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="63d4a-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="63d4a-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="63d4a-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

