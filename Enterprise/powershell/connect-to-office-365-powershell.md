---
title: Подключение к Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/30/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.
ms.openlocfilehash: 0906da2b8773973236bc8cb6ef273d1a14528bfd
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997425"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="d6b30-103">Подключение к Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6b30-103">Connect to Office 365 PowerShell</span></span>

<span data-ttu-id="d6b30-104">PowerShell в Office 365 позволяет управлять параметрами Office 365 из командной строки.</span><span class="sxs-lookup"><span data-stu-id="d6b30-104">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="d6b30-105">Подключение к PowerShell в Office 365 — это простой процесс установки необходимого программного обеспечения и последующего подключения к организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="d6b30-105">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="d6b30-106">Существует две версии модуля PowerShell, которые используются для подключения к Office 365 и управления учетными записями пользователей, группами и лицензиями:</span><span class="sxs-lookup"><span data-stu-id="d6b30-106">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="d6b30-107">Azure Active Directory PowerShell для Graph (командлеты содержат **AzureAD** в своем имени)</span><span class="sxs-lookup"><span data-stu-id="d6b30-107">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="d6b30-108">Модуль Microsoft Azure Active Directory для Windows PowerShell (командлеты содержат **MSol** в своем имени)</span><span class="sxs-lookup"><span data-stu-id="d6b30-108">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="d6b30-109">На момент выхода этой статьи модуль Azure Active Directory PowerShell для Graph не полностью заменяет функции командлетов модуля Microsoft Azure Active Directory для Windows PowerShell при администрировании пользователей, групп и лицензий.</span><span class="sxs-lookup"><span data-stu-id="d6b30-109">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="d6b30-110">Во многих случаях необходимо использовать обе версии.</span><span class="sxs-lookup"><span data-stu-id="d6b30-110">In many cases, you need to use both versions.</span></span> <span data-ttu-id="d6b30-111">Вы можете безопасно установить обе версии на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="d6b30-111">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="d6b30-112">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="d6b30-112">What do you need to know before you begin?</span></span>

<span data-ttu-id="d6b30-113">Ниже приведены версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="d6b30-113">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="d6b30-114">Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="d6b30-114">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="d6b30-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d6b30-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="d6b30-116">Для модуля Azure Active Directory PowerShell для Graph требуется использовать PowerShell версии 5.1 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="d6b30-116">For the Azure Active Directory PowerShell for Graph module, you must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="d6b30-117">Для модуля Microsoft Azure Active Directory для Windows PowerShell требуется использовать PowerShell версии 5.1 или более поздней до PowerShell версии 6.</span><span class="sxs-lookup"><span data-stu-id="d6b30-117">For the Microsoft Azure Active Directory Module for Windows PowerShell module, you must use PowerShell version 5.1 or later up to PowerShell version 6.</span></span> <span data-ttu-id="d6b30-118">Вы не можете использовать PowerShell версии 7.</span><span class="sxs-lookup"><span data-stu-id="d6b30-118">You cannot use PowerShell version 7.</span></span> <span data-ttu-id="d6b30-119">Для Windows 8.1, Windows 8, Windows 7 с пакетом обновления 1 (SP1), Windows Server 2012 R2, Windows Server 2012 и Windows Server 2008 R2 SP1 скачайте и установите [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="d6b30-119">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="d6b30-120">Use a 64-bit version of Windows.</span><span class="sxs-lookup"><span data-stu-id="d6b30-120">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="d6b30-121">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span><span class="sxs-lookup"><span data-stu-id="d6b30-121">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="d6b30-122">Эти процедуры предназначены для пользователей, являющихся участниками роли администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="d6b30-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="d6b30-123">Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="d6b30-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d6b30-124">Подключение к модулю Azure Active Directory PowerShell для Graph</span><span class="sxs-lookup"><span data-stu-id="d6b30-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d6b30-125">Имена командлетов в модуле Azure Active Directory PowerShell для Graph включают компонент **AzureAD**.</span><span class="sxs-lookup"><span data-stu-id="d6b30-125">Commands in the Azure Active Directory PowerShell for Graph module have **AzureAD** in their cmdlet name.</span></span> <span data-ttu-id="d6b30-126">Вы можете установить модуль [Azure Active Directory PowerShell для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) или [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span><span class="sxs-lookup"><span data-stu-id="d6b30-126">You can install the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module or [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span></span>

<span data-ttu-id="d6b30-127">Чтобы выполнить действия, требующие использования новых командлетов в модуле Azure Active Directory PowerShell для Graph, установите его и подключитесь к подписке на Office 365. Вот как это сделать:</span><span class="sxs-lookup"><span data-stu-id="d6b30-127">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="d6b30-128">Информацию о поддержке в различных версиях Microsoft Windows см. в [этой статье](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="d6b30-128">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="d6b30-129">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="d6b30-129">Step 1: Install required software</span></span>

<span data-ttu-id="d6b30-130">These steps are required once on your computer, not every time you connect.</span><span class="sxs-lookup"><span data-stu-id="d6b30-130">These steps are required once on your computer, not every time you connect.</span></span> <span data-ttu-id="d6b30-131">However, you'll likely need to install newer versions of the software periodically.</span><span class="sxs-lookup"><span data-stu-id="d6b30-131">However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="d6b30-132">Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).</span><span class="sxs-lookup"><span data-stu-id="d6b30-132">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="d6b30-133">В командном окне **Администратор: Windows PowerShell** выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="d6b30-133">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="d6b30-134">Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="d6b30-134">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="d6b30-135">Шаг 2. Подключитесь к Azure AD для своей подписки Office 365</span><span class="sxs-lookup"><span data-stu-id="d6b30-135">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="d6b30-136">Чтобы подключиться к Azure AD для своей подписки на Office 365 с помощью имени учетной записи и пароля или с помощью многофакторной проверкой подлинности (MFA), запустите одну из этих команд в командной строке Windows PowerShell (повышенные привилегии не требуются).</span><span class="sxs-lookup"><span data-stu-id="d6b30-136">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="d6b30-137">**Облачная служба Office 365**</span><span class="sxs-lookup"><span data-stu-id="d6b30-137">**Office 365 cloud**</span></span> | <span data-ttu-id="d6b30-138">**Команда**</span><span class="sxs-lookup"><span data-stu-id="d6b30-138">**Command**</span></span> |
| <span data-ttu-id="d6b30-139">Office 365 Worldwide (+GCC)</span><span class="sxs-lookup"><span data-stu-id="d6b30-139">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="d6b30-140">Office 365, предоставляемый 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="d6b30-140">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="d6b30-141">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="d6b30-141">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="d6b30-142">Office 365 для DoD государственных организаций США и Office 365 для GCC High государственных организаций США</span><span class="sxs-lookup"><span data-stu-id="d6b30-142">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="d6b30-143">В диалоговом окне **Вход в учетную запись** введите имя пользователя и пароль своей рабочей или учебной учетной записи Office 365 и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d6b30-143">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="d6b30-144">Если вы используете многофакторную проверку подлинности, следуйте инструкциям в дополнительных диалоговых окнах, чтобы предоставить дополнительные сведения для проверки подлинности, например код проверки.</span><span class="sxs-lookup"><span data-stu-id="d6b30-144">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="d6b30-145">После подключения можно использовать командлеты для [модуля Azure Active Directory PowerShell для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="d6b30-145">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d6b30-146">Подключение к модулю Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6b30-146">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d6b30-147">Имена командлетов в модуле Microsoft Azure Active Directory для Windows PowerShell включают компонент **Msol**.</span><span class="sxs-lookup"><span data-stu-id="d6b30-147">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

<span data-ttu-id="d6b30-148">В PowerShell версии 7 и более поздних версиях не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="d6b30-148">PowerShell version 7 and later do not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d6b30-149">Для PowerShell версии 7 и более поздних версий требуется использовать модуль Azure Active Directory PowerShell для Graph или Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6b30-149">For PowerShell version 7 and later, you must use the Azure Active Directory PowerShell for Graph module or Azure PowerShell.</span></span>

<span data-ttu-id="d6b30-150">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="d6b30-150">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d6b30-151">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6b30-151">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span> 
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="d6b30-152">Шаг 1. Установите необходимое программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="d6b30-152">Step 1: Install required software</span></span>

<span data-ttu-id="d6b30-153">These steps are required once on your computer, not every time you connect.</span><span class="sxs-lookup"><span data-stu-id="d6b30-153">These steps are required once on your computer, not every time you connect.</span></span> <span data-ttu-id="d6b30-154">However, you'll likely need to install newer versions of the software periodically.</span><span class="sxs-lookup"><span data-stu-id="d6b30-154">However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="d6b30-155">Если вы не используете Windows 10, установите 64-разрядную версию помощника по входу в Microsoft Online Services: [Помощник по входу в Microsoft Online Services для ИТ-специалистов RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="d6b30-155">If you are not running Windows 10, install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="d6b30-156">Чтобы установить модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="d6b30-156">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="d6b30-157">Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).</span><span class="sxs-lookup"><span data-stu-id="d6b30-157">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="d6b30-158">Выполните команду **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="d6b30-158">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="d6b30-159">Если отобразится запрос на установку поставщика NuGet, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="d6b30-159">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="d6b30-160">Если отобразится запрос на установку модуля из репозитория PSGallery, введите **Y** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="d6b30-160">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="d6b30-161">Шаг 2. Подключитесь к Azure AD для своей подписки Office 365</span><span class="sxs-lookup"><span data-stu-id="d6b30-161">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="d6b30-162">Чтобы подключиться к Azure AD для своей подписки на Office 365 с помощью имени учетной записи и пароля или с помощью многофакторной проверкой подлинности (MFA), запустите одну из этих команд в командной строке Windows PowerShell (повышенные привилегии не требуются).</span><span class="sxs-lookup"><span data-stu-id="d6b30-162">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="d6b30-163">**Облачная служба Office 365**</span><span class="sxs-lookup"><span data-stu-id="d6b30-163">**Office 365 cloud**</span></span> | <span data-ttu-id="d6b30-164">**Команда**</span><span class="sxs-lookup"><span data-stu-id="d6b30-164">**Command**</span></span> |
| <span data-ttu-id="d6b30-165">Office 365 Worldwide (+GCC)</span><span class="sxs-lookup"><span data-stu-id="d6b30-165">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="d6b30-166">Office 365, предоставляемый 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="d6b30-166">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="d6b30-167">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="d6b30-167">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="d6b30-168">Office 365 для DoD государственных организаций США и Office 365 для GCC High государственных организаций США</span><span class="sxs-lookup"><span data-stu-id="d6b30-168">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="d6b30-169">В диалоговом окне **Вход в учетную запись** введите имя пользователя и пароль своей рабочей или учебной учетной записи Office 365 и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d6b30-169">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="d6b30-170">Если вы используете многофакторную проверку подлинности, следуйте инструкциям в дополнительных диалоговых окнах, чтобы предоставить дополнительные сведения для проверки подлинности, например код проверки.</span><span class="sxs-lookup"><span data-stu-id="d6b30-170">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="d6b30-171">Как проверить, все ли получилось?</span><span class="sxs-lookup"><span data-stu-id="d6b30-171">How do you know this worked?</span></span>

<span data-ttu-id="d6b30-172">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="d6b30-172">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="d6b30-173">A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span><span class="sxs-lookup"><span data-stu-id="d6b30-173">A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="d6b30-174">Если возникают ошибки, просмотрите список возможных причин ниже.</span><span class="sxs-lookup"><span data-stu-id="d6b30-174">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="d6b30-175">**Распространенная проблема  неправильный пароль.**.</span><span class="sxs-lookup"><span data-stu-id="d6b30-175">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="d6b30-176">Еще раз выполните шаг 2,</span><span class="sxs-lookup"><span data-stu-id="d6b30-176">Run Step 2 again.</span></span> <span data-ttu-id="d6b30-177">внимательно проверив вводимое имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="d6b30-177">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="d6b30-178">**Для работы модуля Microsoft Azure Active Directory для Windows PowerShell необходимо, чтобы на вашем компьютере был включен компонент Microsoft .NET Framework 3.5.* x*. Скорее всего, на вашем компьютере установлена более новая версия этого компонента (например, 4 или 4.5.\* x\*), но вы можете включить или отключить режим обратной совместимости с более ранними версиями платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6b30-178">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="d6b30-179">Дополнительную информацию см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="d6b30-179">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="d6b30-180">[Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)</span><span class="sxs-lookup"><span data-stu-id="d6b30-180">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="d6b30-181">[Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="d6b30-181">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="d6b30-182">[Установка платформы .NET Framework 3.5 на Windows 10, Windows 8.1 и Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10) (Windows 10, Windows 8.1 и Windows 8)</span><span class="sxs-lookup"><span data-stu-id="d6b30-182">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="d6b30-183">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span><span class="sxs-lookup"><span data-stu-id="d6b30-183">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="d6b30-184">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d6b30-184">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="d6b30-185">Если возвращенный номер версии меньше значения 1.0.8070.2, удалите модуль Microsoft Azure Active Directory для Windows PowerShell и установите его на шаге 1 выше.</span><span class="sxs-lookup"><span data-stu-id="d6b30-185">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install from Step 1 above.</span></span>

- <span data-ttu-id="d6b30-186">\*\*Если при подключении возникнет ошибка, ознакомьтесь с \*\*[этой статьей](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="d6b30-186">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
- <span data-ttu-id="d6b30-187">**Если возникнет ошибка "Get-Item: не удается найти путь", используйте следующую команду:**</span><span class="sxs-lookup"><span data-stu-id="d6b30-187">**If you receive a "Get-Item : Cannot find path" error, use this command:**</span></span> 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a><span data-ttu-id="d6b30-188">См. также</span><span class="sxs-lookup"><span data-stu-id="d6b30-188">See also</span></span>

- [<span data-ttu-id="d6b30-189">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="d6b30-189">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d6b30-190">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6b30-190">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="d6b30-191">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6b30-191">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
