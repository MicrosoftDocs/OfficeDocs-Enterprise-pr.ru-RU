---
title: Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Сводка: подключение Windows PowerShell ко всем службам Office 365 в отдельном окне Windows PowerShell.'
ms.openlocfilehash: 3f6153d5ea8b88d8c6853dbbe597f2cf7cc62fab
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573973"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="23d18-103">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="23d18-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="23d18-104">**Сводка:** Вместо того чтобы управлять различными службами Office 365 в разных окнах консоли PowerShell, можно подключаться ко всем службам Office 365 и управлять ими из одного окна консоли.</span><span class="sxs-lookup"><span data-stu-id="23d18-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="23d18-105">При использовании PowerShell для управления Office 365 можно одновременно открыть до пяти разных сеансов Windows PowerShell, соответствующих центру администрирования Microsoft 365, SharePoint Online, Exchange Online, Skype для бизнеса Online и безопасности. &amp; Центр соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="23d18-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="23d18-106">С пятью методами подключения, которые находятся в разных сеансах Windows PowerShell, ваш рабочий стол может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="23d18-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Пять консолей Windows PowerShell, работающих одновременно](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="23d18-108">Это не является оптимальным для управления Office 365, так как вы не можете обмениваться данными между этими пятью окнами для управления в нескольких службах.</span><span class="sxs-lookup"><span data-stu-id="23d18-108">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="23d18-109">В этом разделе описывается, как использовать один экземпляр Windows PowerShell, на котором можно управлять Office 365, Skype для бизнеса Online, Exchange Online, SharePoint Online и центром обеспечения безопасности &amp; .</span><span class="sxs-lookup"><span data-stu-id="23d18-109">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="23d18-110">В настоящее время эта статья содержит только команды для подключения к облаку Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="23d18-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="23d18-111">Дополнительные примечания содержат ссылки на статьи со сведениями о подключении к другим облакам Office 365.</span><span class="sxs-lookup"><span data-stu-id="23d18-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="23d18-112">До начала работы</span><span class="sxs-lookup"><span data-stu-id="23d18-112">Before you begin</span></span>

<span data-ttu-id="23d18-113">Прежде чем управлять всеми Office 365 из одного экземпляра Windows PowerShell, примите во внимание следующие предварительные требования:</span><span class="sxs-lookup"><span data-stu-id="23d18-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="23d18-114">Рабочая или учебная учетная запись Office 365, используемая для выполнения этих процедур, должна быть членом роли администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="23d18-114">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="23d18-115">Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="23d18-115">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="23d18-116">Это требование для Office 365 PowerShell, не обязательно для всех остальных служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="23d18-116">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="23d18-117">Ниже приведены 64-разрядные версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="23d18-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="23d18-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="23d18-118">Windows 10</span></span>
    
  - <span data-ttu-id="23d18-119">Windows 8.1 или Windows 8</span><span class="sxs-lookup"><span data-stu-id="23d18-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="23d18-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="23d18-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="23d18-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="23d18-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="23d18-122">Windows Server 2012 R2 или Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="23d18-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="23d18-123">Windows 7 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="23d18-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="23d18-124">Windows Server 2008 R2 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="23d18-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="23d18-125">\*Необходимо установить Microsoft .NET Framework 4,5. *x* , а затем — Windows management Framework 3,0 или Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="23d18-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="23d18-126">Дополнительные сведения см. [в статье Установка .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) и [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="23d18-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="23d18-127">Необходимо использовать 64-разрядную версию Windows из-за требований для модуля Skype для бизнеса Online и одного из модулей Office 365.</span><span class="sxs-lookup"><span data-stu-id="23d18-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="23d18-128">Необходимо установить модули, необходимые для Azure AD, SharePoint Online и Skype для бизнеса Online:</span><span class="sxs-lookup"><span data-stu-id="23d18-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="23d18-129">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="23d18-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="23d18-130">Командная консоль SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="23d18-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="23d18-131">Skype для бизнеса Online, модуль Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="23d18-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="23d18-132">Необходимо настроить Windows PowerShell, чтобы выполнять подписанные сценарии для Skype для бизнеса Online, Exchange Online и центра безопасности &amp; и соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="23d18-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="23d18-133">Для этого выполните следующую команду в сеансе Windows PowerShell с повышенными привилегиями (для этого выберите пункт **Запуск от имени администратора**).</span><span class="sxs-lookup"><span data-stu-id="23d18-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="23d18-134">Шаги подключения при использовании пароля</span><span class="sxs-lookup"><span data-stu-id="23d18-134">Connection steps when using a password</span></span>

<span data-ttu-id="23d18-135">Ниже описаны действия, которые необходимо выполнить для подключения ко всем службам в отдельном окне PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23d18-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="23d18-136">Откройте Windows PowerShell от имени администратора (используйте **Запуск от имени администратора**).</span><span class="sxs-lookup"><span data-stu-id="23d18-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="23d18-137">Выполните эту команду и введите учетные данные рабочей или учебной учетной записи Office 365.</span><span class="sxs-lookup"><span data-stu-id="23d18-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="23d18-138">Выполните эту команду для подключения к Azure Active Directory (AD) с помощью модуля PowerShell Azure Active Directory PowerShell для Graph.</span><span class="sxs-lookup"><span data-stu-id="23d18-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="23d18-139">Кроме того, если вы используете модуль Microsoft Azure Active Directory Module для Windows PowerShell, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="23d18-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="23d18-140">Выполните указанные ниже команды, чтобы подключиться к SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="23d18-140">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="23d18-141">Замените _ \<домаинхост_гт__ на фактическое значение для вашего домена.</span><span class="sxs-lookup"><span data-stu-id="23d18-141">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="23d18-142">например, для "litwareinc.onmicrosoft.com" значение _ \<домаинхост_гт__ — "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="23d18-142">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="23d18-143">Выполните приведенные ниже команды, чтобы подключиться к Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="23d18-143">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="23d18-144">Предупреждение об увеличении `WSMan NetworkDelayms` значения ожидается при первом подключении и должно быть проигнорировано.</span><span class="sxs-lookup"><span data-stu-id="23d18-144">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="23d18-145">Выполните эти команды для подключения к Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="23d18-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="23d18-146">Чтобы подключиться к Exchange Online для офисов Office 365, отличных от мира, ознакомьтесь со статьей [Подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="23d18-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="23d18-147">Выполните приведенные ниже команды, чтобы подключиться &amp; к центру соответствия требованиям безопасности.</span><span class="sxs-lookup"><span data-stu-id="23d18-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="23d18-148">Чтобы подключиться к центру соответствия &amp; требованиям безопасности для облаков Office 365, отличных от мира, ознакомьтесь со статьей [подключение к Office 365 Security _Амп_ The PowerShell Center](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="23d18-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="23d18-149">Ниже приведены все команды в отдельном блоке при использовании модуля Azure Active Directory PowerShell для Graph.</span><span class="sxs-lookup"><span data-stu-id="23d18-149">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="23d18-150">Укажите имя узла домена, а затем выполните все сразу.</span><span class="sxs-lookup"><span data-stu-id="23d18-150">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="23d18-151">Кроме того, здесь приведены все команды в едином блоке при использовании модуля Microsoft Azure Active Directory для модуля Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23d18-151">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="23d18-152">Укажите имя узла домена, а затем выполните все сразу.</span><span class="sxs-lookup"><span data-stu-id="23d18-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="23d18-153">Когда вы будете готовы закрыть окно Windows PowerShell, выполните следующую команду, чтобы удалить активные сеансы связи с Skype для бизнеса Online, Exchange Online, SharePoint Online и центром безопасности &amp; и соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="23d18-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="23d18-154">Шаги подключения при использовании многофакторной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="23d18-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="23d18-155">Ниже приведены все команды в едином блоке для подключения к Azure AD, SharePoint Online и Skype для Буинесс с использованием многофакторной проверки подлинности в отдельном окне с помощью модуля Azure Active Directory PowerShell для Graph.</span><span class="sxs-lookup"><span data-stu-id="23d18-155">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="23d18-156">Укажите имя участника-пользователя (UPN) для учетной записи пользователя и имя узла домена, а затем запустите их в один раз.</span><span class="sxs-lookup"><span data-stu-id="23d18-156">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="23d18-157">Кроме того, при использовании модуля Microsoft Azure Active Directory для Windows PowerShell можно использовать и все команды.</span><span class="sxs-lookup"><span data-stu-id="23d18-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="23d18-158">Для Exchange Online и центра соответствия &amp; требованиям безопасности ознакомьтесь со следующими разделами, чтобы подключиться с использованием многофакторной проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="23d18-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="23d18-159">Подключение к Exchange Online PowerShell с помощью многофакторной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="23d18-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="23d18-160">Подключение к PowerShell центра безопасности _Амп_ для Office 365 с использованием многофакторной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="23d18-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="23d18-161">Обратите внимание, что в обоих случаях необходимо подключаться с помощью отдельных сеансов удаленного модуля PowerShell Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="23d18-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="23d18-162">См. также</span><span class="sxs-lookup"><span data-stu-id="23d18-162">See also</span></span>

- [<span data-ttu-id="23d18-163">Подключение к Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="23d18-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="23d18-164">Управление SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="23d18-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="23d18-165">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="23d18-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="23d18-166">Использование Windows PowerShell для создания отчетов в Office 365</span><span class="sxs-lookup"><span data-stu-id="23d18-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
