---
title: Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Сводка: подключение Windows PowerShell ко всем службам Office 365 в отдельном окне Windows PowerShell.'
ms.openlocfilehash: 47fd2be814b446cf12b136e359cdadc9374a7ab6
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208810"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="57b34-103">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="57b34-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="57b34-104">При использовании PowerShell для управления Office 365 можно одновременно открыть до пяти разных сеансов Windows PowerShell, соответствующих центру администрирования Microsoft 365, SharePoint Online, Exchange Online, Skype для бизнеса Online, Microsoft Teams и центре безопасности и &amp; соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="57b34-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="57b34-105">С пятью методами подключения, которые находятся в разных сеансах Windows PowerShell, ваш рабочий стол может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="57b34-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Пять консолей Windows PowerShell, работающих одновременно](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="57b34-107">Это не является оптимальным для управления Office 365, так как вы не можете обмениваться данными между этими пятью окнами для управления в нескольких службах.</span><span class="sxs-lookup"><span data-stu-id="57b34-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="57b34-108">В этом разделе описывается, как использовать один экземпляр Windows PowerShell, с которого вы можете управлять Office 365, Skype для бизнеса Online, Exchange Online, SharePoint Online, Microsoft Teams и центром безопасности и &amp; соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="57b34-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="57b34-109">В настоящее время эта статья содержит только команды для подключения к облаку Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="57b34-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="57b34-110">Дополнительные примечания содержат ссылки на статьи со сведениями о подключении к другим облакам Office 365.</span><span class="sxs-lookup"><span data-stu-id="57b34-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="57b34-111">Подготовка</span><span class="sxs-lookup"><span data-stu-id="57b34-111">Before you begin</span></span>

<span data-ttu-id="57b34-112">Прежде чем управлять всеми Office 365 из одного экземпляра Windows PowerShell, примите во внимание следующие предварительные требования:</span><span class="sxs-lookup"><span data-stu-id="57b34-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="57b34-113">Рабочая или учебная учетная запись Office 365, используемая для выполнения этих процедур, должна быть членом роли администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="57b34-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="57b34-114">Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="57b34-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="57b34-115">Это требование для Office 365 PowerShell, не обязательно для всех остальных служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="57b34-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="57b34-116">Ниже приведены 64-разрядные версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="57b34-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="57b34-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="57b34-117">Windows 10</span></span>
    
  - <span data-ttu-id="57b34-118">Windows 8.1 или Windows 8</span><span class="sxs-lookup"><span data-stu-id="57b34-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="57b34-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="57b34-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="57b34-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="57b34-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="57b34-121">Windows Server 2012 R2 или Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="57b34-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="57b34-122">Windows 7 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="57b34-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="57b34-123">Windows Server 2008 R2 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="57b34-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="57b34-124">\*Необходимо установить Microsoft .NET Framework 4,5. *x* , а затем — Windows management Framework 3,0 или Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="57b34-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="57b34-125">Дополнительные сведения см. [в статье Установка .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) и [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="57b34-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="57b34-126">Необходимо использовать 64-разрядную версию Windows из-за требований для модуля Skype для бизнеса Online и одного из модулей Office 365.</span><span class="sxs-lookup"><span data-stu-id="57b34-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="57b34-127">Необходимо установить модули, необходимые для Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype для бизнеса Online и teams:</span><span class="sxs-lookup"><span data-stu-id="57b34-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="57b34-128">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="57b34-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="57b34-129">Командная консоль SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="57b34-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="57b34-130">Skype для бизнеса Online, модуль Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="57b34-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="57b34-131">Exchange Online PowerShell v2</span><span class="sxs-lookup"><span data-stu-id="57b34-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="57b34-132">Общие сведения о Teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="57b34-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="57b34-133">Необходимо настроить Windows PowerShell, чтобы выполнять подписанные сценарии для Skype для бизнеса Online и &amp; центра соответствия требованиям безопасности.</span><span class="sxs-lookup"><span data-stu-id="57b34-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="57b34-134">Для этого выполните следующую команду в сеансе Windows PowerShell с повышенными привилегиями (для этого выберите пункт **Запуск от имени администратора**).</span><span class="sxs-lookup"><span data-stu-id="57b34-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="57b34-135">Шаги подключения при использовании пароля</span><span class="sxs-lookup"><span data-stu-id="57b34-135">Connection steps when using a password</span></span>

<span data-ttu-id="57b34-136">Ниже описаны действия, которые необходимо выполнить для подключения ко всем службам в отдельном окне PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57b34-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="57b34-137">Откройте командную консоль Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57b34-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="57b34-138">Выполните указанную ниже команду и введите учетные данные рабочей или учебной учетной записи Office 365.</span><span class="sxs-lookup"><span data-stu-id="57b34-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="57b34-139">Выполните эту команду, чтобы подключиться к Azure AD с помощью модуля PowerShell Azure Active Directory PowerShell для Graph.</span><span class="sxs-lookup"><span data-stu-id="57b34-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="57b34-140">Кроме того, если вы используете модуль Microsoft Azure Active Directory Module для Windows PowerShell, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="57b34-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="57b34-141">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="57b34-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="57b34-142">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57b34-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="57b34-143">Выполните указанные ниже команды, чтобы подключиться к SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="57b34-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="57b34-144">Замените _ \< домаинхост>_ на фактическое значение для вашего домена.</span><span class="sxs-lookup"><span data-stu-id="57b34-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="57b34-145">Например, для "litwareinc.onmicrosoft.com" _ \< домаинхост>_ значение "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="57b34-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="57b34-146">Выполните приведенные ниже команды, чтобы подключиться к Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="57b34-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="57b34-147">Предупреждение об увеличении `WSMan NetworkDelayms` значения ожидается при первом подключении и должно быть проигнорировано.</span><span class="sxs-lookup"><span data-stu-id="57b34-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="57b34-148">Выполните эту команду, чтобы подключиться к Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="57b34-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="57b34-149">Чтобы подключиться к Exchange Online для Office 365 для облаков, отличных от международных, используйте параметр **-ексчанжеенвиронментнаме** .</span><span class="sxs-lookup"><span data-stu-id="57b34-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="57b34-150">Для получения дополнительных сведений обратитесь [к раздел Connect – ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) .</span><span class="sxs-lookup"><span data-stu-id="57b34-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="57b34-151">Выполните эти команды для подключения к PowerShell Teams PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57b34-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="57b34-152">Чтобы подключиться к облакам Microsoft Teams, не по всему миру, ознакомьтесь с разделом [Connect – MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="57b34-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="57b34-153">Выполните приведенные ниже команды, чтобы подключиться к &amp; центру соответствия требованиям безопасности.</span><span class="sxs-lookup"><span data-stu-id="57b34-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="57b34-154">Чтобы подключиться к &amp; центру соответствия требованиям безопасности для облаков office 365, отличных от мира, ознакомьтесь со статьей [Подключение к Office 365 Security & центра соответствия требованиям PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="57b34-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="57b34-155">Ниже приведены все команды в отдельном блоке при использовании модуля Azure Active Directory PowerShell для Graph.</span><span class="sxs-lookup"><span data-stu-id="57b34-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="57b34-156">Укажите имя узла домена, а затем выполните все сразу.</span><span class="sxs-lookup"><span data-stu-id="57b34-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="57b34-157">Кроме того, здесь приведены все команды в едином блоке при использовании модуля Microsoft Azure Active Directory для модуля Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57b34-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="57b34-158">Укажите имя узла домена, а затем выполните все сразу.</span><span class="sxs-lookup"><span data-stu-id="57b34-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="57b34-159">Когда вы будете готовы закрыть окно Windows PowerShell, выполните следующую команду, чтобы удалить активные сеансы в Skype для бизнеса Online, SharePoint Online, &amp; центре безопасности и соответствия требованиям teams:</span><span class="sxs-lookup"><span data-stu-id="57b34-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="57b34-160">Шаги подключения при использовании многофакторной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="57b34-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="57b34-161">Ниже приведены все команды в едином блоке для подключения к Azure AD, SharePoint Online, Skype для бизнеса, Exchange Online и Teams с использованием многофакторной проверки подлинности в отдельном окне с помощью модуля Azure Active Directory PowerShell для Graph.</span><span class="sxs-lookup"><span data-stu-id="57b34-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="57b34-162">Укажите имя участника-пользователя (UPN) для учетной записи пользователя и имя узла домена, а затем запустите их в один раз.</span><span class="sxs-lookup"><span data-stu-id="57b34-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="57b34-163">Кроме того, при использовании модуля Microsoft Azure Active Directory для Windows PowerShell можно использовать и все команды.</span><span class="sxs-lookup"><span data-stu-id="57b34-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="57b34-164">В центре безопасности для обеспечения соответствия требованиям Узнайте, как подключить многофакторную проверку подлинности с помощью многофакторной проверки подлинности для &amp; подключения к [Office 365 Security & центре соответствия требованиям в PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) .</span><span class="sxs-lookup"><span data-stu-id="57b34-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="57b34-165">См. также</span><span class="sxs-lookup"><span data-stu-id="57b34-165">See also</span></span>

- [<span data-ttu-id="57b34-166">Подключение к Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="57b34-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="57b34-167">Управление SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="57b34-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="57b34-168">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="57b34-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="57b34-169">Использование Windows PowerShell для создания отчетов в Office 365</span><span class="sxs-lookup"><span data-stu-id="57b34-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
