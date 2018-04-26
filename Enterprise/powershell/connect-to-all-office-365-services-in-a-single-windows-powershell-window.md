---
title: Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/23/2018
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
description: 'Сводка: Подключение Windows PowerShell для всех служб Office 365 в одном окне Windows PowerShell.'
ms.openlocfilehash: 7e3a3ecbb0526c88392848cf39b59b40f1f4c80c
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="439ab-103">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="439ab-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="439ab-104">**Сводка:** Вместо управление различных службах Office 365 в отдельной консоли windows PowerShell можно подключиться ко всем службам Office 365 и управлять ими из одного окна консоли.</span><span class="sxs-lookup"><span data-stu-id="439ab-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="439ab-p101">При использовании PowerShell для управления Office 365, его можно установить до пяти различных Windows PowerShell открытые в то же время, соответствующий центра администрирования Office 365, SharePoint Online, Exchange Online, Скайп для бизнеса в Интернет и безопасности &amp;Центре соответствия требованиям. С помощью пяти разные способы подключения в отдельных сеансах Windows PowerShell к рабочему столу может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="439ab-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Пять консолей Windows PowerShell, работающих одновременно](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="439ab-p102">Это не является оптимальным для управления Office 365, так как не удается обмен данными между этих пяти windows для управления между службами. В этом разделе описывается, как использовать один экземпляр Windows PowerShell, из которого можно управлять Office 365, Скайп для бизнеса в Интернет, Exchange Online, SharePoint Online и безопасность &amp; центре соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="439ab-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="439ab-110">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="439ab-110">Before you begin</span></span>
<span data-ttu-id="439ab-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="439ab-111"></span></span>

<span data-ttu-id="439ab-112">Прежде чем все Office 365 можно управлять из одного экземпляра Windows PowerShell, необходимо учитывайте следующие требования:</span><span class="sxs-lookup"><span data-stu-id="439ab-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="439ab-p103">Office 365 работы или школе учетной записи, используемой для этих процедур потребностей для быть участником роли администратора Office 365. Дополнительные сведения см в [роли администраторов об Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). В этом является обязательным требованием для Office 365 PowerShell, а не обязательно для всех других служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="439ab-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="439ab-116">Ниже приведены 64-разрядные версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="439ab-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="439ab-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="439ab-117">Windows 10</span></span>
    
  - <span data-ttu-id="439ab-118">Windows 8.1 или Windows 8</span><span class="sxs-lookup"><span data-stu-id="439ab-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="439ab-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="439ab-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="439ab-120">Windows Server 2012 R2 или Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="439ab-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="439ab-121">Windows 7 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="439ab-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="439ab-122">Windows Server 2008 R2 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="439ab-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="439ab-p104">Необходимо установить Microsoft .NET Framework 4.5. *x* и затем либо Windows Management Framework 3.0 или Windows Management Framework 4.0. Для получения дополнительных сведений см [установки .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) и [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="439ab-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="439ab-125">Необходимо использовать 64-разрядной версии Windows из-за требования к Скайп для бизнеса в Интернет в модуле и один из модулей Office 365.</span><span class="sxs-lookup"><span data-stu-id="439ab-125">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="439ab-126">Требуется ли установить модули, которые необходимы для Azure AD SharePoint Online и Скайп для бизнеса в Интернет:</span><span class="sxs-lookup"><span data-stu-id="439ab-126">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="439ab-127">Azure Active Directory версии 2</span><span class="sxs-lookup"><span data-stu-id="439ab-127">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md#ConnectV2)
   - [<span data-ttu-id="439ab-128">Командная консоль SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="439ab-128">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="439ab-129">Скайп для бизнеса через Интернет, модуля Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="439ab-129">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="439ab-p105">Windows PowerShell необходимо настроить для запуска сценариев со знаком для Скайп для бизнеса в Интернет, Exchange Online и безопасность &amp; центре соответствия требованиям. Для этого выполните следующую команду в сеансе Windows PowerShell с повышенными привилегиями (окно Windows PowerShell можно открыть, выбрав **Запуск от имени администратора**).</span><span class="sxs-lookup"><span data-stu-id="439ab-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="439ab-132">Действия подключения при с помощью пароля</span><span class="sxs-lookup"><span data-stu-id="439ab-132">Connection steps when using a password</span></span>
<span data-ttu-id="439ab-133"><a name="ConnStepsPassword"> </a></span><span class="sxs-lookup"><span data-stu-id="439ab-133"></span></span>

<span data-ttu-id="439ab-134">Далее приведены шаги для подключения к службам в одном окне PowerShell.</span><span class="sxs-lookup"><span data-stu-id="439ab-134">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="439ab-135">Откройте Windows PowerShell с правами администратора ( **Запуск от имени администратора**использования).</span><span class="sxs-lookup"><span data-stu-id="439ab-135">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="439ab-136">Выполните следующую команду и введите данные Office 365 или школе учетные данные учетной записи.</span><span class="sxs-lookup"><span data-stu-id="439ab-136">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="439ab-137">Выполните эту команду, чтобы подключиться к Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="439ab-137">Run this command to connect to Azure Active Directory (AD).</span></span>
    
  ```
   Connect-AzureAD -Credential $credential
  ```

4. <span data-ttu-id="439ab-p106">Выполните следующие команды для подключения к SharePoint Online. Замените _ \<domainhost >_ с фактическое значение для вашего домена. Например, `litwareinc.onmicrosoft.com`, _ \<domainhost >_ значение — `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="439ab-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="439ab-p107">Выполните следующие команды для подключения к Скайп для бизнеса в Интернет. Предупреждение о том, увеличение `WSMan NetworkDelayms` впервые ожидается значение подключения и можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="439ab-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="439ab-143">Выполните следующие команды для подключения к Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="439ab-143">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. <span data-ttu-id="439ab-144">Выполните следующие команды для подключения к безопасности &amp; центре соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="439ab-144">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

<span data-ttu-id="439ab-p108">Ниже приведены все команды в один блок. Укажите имя вашего домена узла и затем использовать их для работы всех за один раз.</span><span class="sxs-lookup"><span data-stu-id="439ab-p108">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```
<span data-ttu-id="439ab-147">Когда вы будете готовы закрыть все окна Windows PowerShell, выполните следующую команду, чтобы удалить активных сеансов для Скайп для бизнеса в Интернет, Exchange Online, SharePoint Online и безопасность &amp; центре соответствия требованиям:</span><span class="sxs-lookup"><span data-stu-id="439ab-147">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="439ab-148">Действия подключения при использовании многофакторной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="439ab-148">Connection steps when using multi-factor authentication</span></span>
<span data-ttu-id="439ab-149"><a name="ConnStepsMFA"> </a></span><span class="sxs-lookup"><span data-stu-id="439ab-149"></span></span>

<span data-ttu-id="439ab-p109">Ниже приведены все команды в один блок для подключения к Azure AD SharePoint Online и Скайп для Buiness с помощью многофакторной проверки подлинности в одном окне. Укажите имя участника (UPN) имя пользователя учетной записи глобального администратора и доменное имя узла, а затем использовать их для работы всех за один раз.</span><span class="sxs-lookup"><span data-stu-id="439ab-p109">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="439ab-152">Exchange Online и системы безопасности &amp; центре соответствия требованиям в следующих разделах подключиться, используя многофакторной проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="439ab-152">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="439ab-153">Подключение к Exchange Online PowerShell с помощью многофакторной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="439ab-153">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="439ab-154">Подключение к Office 365 безопасности & PowerShell центр соответствия требованиям, с помощью многофакторной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="439ab-154">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="439ab-155">Обратите внимание, что в обоих случаях, необходимо подключиться, используя отдельные сеансы модуля Exchange Online удаленного PowerShell.</span><span class="sxs-lookup"><span data-stu-id="439ab-155">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="439ab-156">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="439ab-156">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="439ab-157">См. также</span><span class="sxs-lookup"><span data-stu-id="439ab-157">See also</span></span>

- [<span data-ttu-id="439ab-158">Подключение к Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="439ab-158">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="439ab-159">Управление SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="439ab-159">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="439ab-160">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="439ab-160">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="439ab-161">Использование Windows PowerShell для создания отчетов в Office 365</span><span class="sxs-lookup"><span data-stu-id="439ab-161">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
