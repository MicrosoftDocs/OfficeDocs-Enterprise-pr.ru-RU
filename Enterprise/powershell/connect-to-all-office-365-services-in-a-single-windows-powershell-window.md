---
title: Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="8d801-103">Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d801-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="8d801-104">**Сводка:** Вместо управление различных службах Office 365 в отдельной консоли windows PowerShell можно подключиться ко всем службам Office 365 и управлять ими из одного окна консоли.</span><span class="sxs-lookup"><span data-stu-id="8d801-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="8d801-p101">При использовании PowerShell для управления Office 365, его можно установить до пяти различных Windows PowerShell открытые в то же время, соответствующий центра администрирования Office 365, SharePoint Online, Exchange Online, Скайп для бизнеса в Интернет и безопасности &amp;Центре соответствия требованиям. С помощью пяти разные способы подключения в отдельных сеансах Windows PowerShell к рабочему столу может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8d801-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Пять консолей Windows PowerShell, работающих одновременно](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="8d801-p102">Это не является оптимальным для управления Office 365, так как не удается обмен данными между этих пяти windows для управления между службами. В этом разделе описывается, как использовать один экземпляр Windows PowerShell, из которого можно управлять Office 365, Скайп для бизнеса в Интернет, Exchange Online, SharePoint Online и безопасность &amp; центре соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="8d801-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="8d801-110">В этой статье — в процессе обновления для использования модуля Azure Active Directory версии 2 PowerShell, а также для многофакторная проверка подлинности (многофакторной проверкой Подлинности).</span><span class="sxs-lookup"><span data-stu-id="8d801-110">This article is in the process of being updated to use the Azure Active Directory V2 PowerShell module and for multifactor authentication (MFA).</span></span>
>
  
## <a name="before-you-begin"></a><span data-ttu-id="8d801-111">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="8d801-111">Before you begin</span></span>
<span data-ttu-id="8d801-112"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="8d801-112"></span></span>

<span data-ttu-id="8d801-113">Прежде чем все Office 365 можно управлять из одного экземпляра Windows PowerShell, необходимо учитывайте следующие требования:</span><span class="sxs-lookup"><span data-stu-id="8d801-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="8d801-p103">Office 365 работы или школе учетной записи, используемой для этих процедур потребностей для быть участником роли администратора Office 365. Дополнительные сведения см в [роли администраторов об Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). В этом является обязательным требованием для Office 365 PowerShell, а не обязательно для всех других служб Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d801-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="8d801-117">Ниже приведены 64-разрядные версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="8d801-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="8d801-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8d801-118">Windows 10</span></span>
    
  - <span data-ttu-id="8d801-119">Windows 8.1 или Windows 8</span><span class="sxs-lookup"><span data-stu-id="8d801-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="8d801-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8d801-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="8d801-121">Windows Server 2012 R2 или Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8d801-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="8d801-122">Windows 7 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="8d801-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="8d801-123">Windows Server 2008 R2 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="8d801-123">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="8d801-p104">Необходимо установить Microsoft .NET Framework 4.5. *x* и затем либо Windows Management Framework 3.0 или Windows Management Framework 4.0. Для получения дополнительных сведений см [установки .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) и [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="8d801-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="8d801-126">Необходимо использовать 64-разрядной версии Windows из-за требования к Скайп для бизнеса в Интернет в модуле и один из модулей Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d801-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="8d801-127">Требуется ли установить модули, которые необходимы для Office 365, SharePoint Online и Скайп для бизнеса в Интернет:</span><span class="sxs-lookup"><span data-stu-id="8d801-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="8d801-128">Microsoft Online службы помощник по входу для ИТ-специалистов RTW</span><span class="sxs-lookup"><span data-stu-id="8d801-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="8d801-129">Windows Azure Active Directory модуль для Windows PowerShell (64-разрядная версия) с помощью команды **Install-модуль MSOnline** в командной строке с повышенными привилегиями PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d801-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="8d801-130">Командная консоль SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8d801-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="8d801-131">Скайп для бизнеса через Интернет, модуля Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d801-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="8d801-p105">Windows PowerShell необходимо настроить для запуска сценариев со знаком для Скайп для бизнеса в Интернет, Exchange Online и безопасность &amp; центре соответствия требованиям. Для этого выполните следующую команду в сеансе Windows PowerShell с повышенными привилегиями (окно Windows PowerShell можно открыть, выбрав **Запуск от имени администратора**).</span><span class="sxs-lookup"><span data-stu-id="8d801-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a><span data-ttu-id="8d801-134">Действия подключения</span><span class="sxs-lookup"><span data-stu-id="8d801-134">Connection steps</span></span>
<span data-ttu-id="8d801-135"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="8d801-135"></span></span>

<span data-ttu-id="8d801-136">Далее приведены шаги для подключения к службам в одном окне PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d801-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="8d801-137">Откройте Windows PowerShell с правами администратора ( **Запуск от имени администратора**использования).</span><span class="sxs-lookup"><span data-stu-id="8d801-137">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="8d801-138">Выполните следующую команду и введите данные Office 365 или школе учетные данные учетной записи.</span><span class="sxs-lookup"><span data-stu-id="8d801-138">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="8d801-139">Выполните следующие команды для подключения к Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d801-139">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="8d801-p106">Выполните следующие команды для подключения к SharePoint Online. Замените _ \<domainhost >_ с фактическое значение для вашего домена. Например, `litwareinc.onmicrosoft.com`, _ \<domainhost >_ значение — `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="8d801-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="8d801-p107">Выполните следующие команды для подключения к Скайп для бизнеса в Интернет. Предупреждение о том, увеличение `WSMan NetworkDelayms` впервые ожидается значение подключения и можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="8d801-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="8d801-145">Выполните следующие команды для подключения к Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="8d801-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="8d801-146">Выполните следующие команды для подключения к безопасности &amp; центре соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="8d801-146">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="8d801-p108">Текст префикса «копия» добавляется *все* безопасности &amp; имена центре соответствия требованиям, могут выполняться командлеты, который существует в Exchange Online и безопасность &amp; центре соответствия требованиям в том же сеансе Windows PowerShell. Например, **Get-RoleGroup** становится **Get-ccRoleGroup** в системы &amp; центре соответствия требованиям.</span><span class="sxs-lookup"><span data-stu-id="8d801-p108">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="8d801-p109">Ниже приведены все команды в один блок. Укажите имя вашего домена узла и затем использовать их для работы всех за один раз.</span><span class="sxs-lookup"><span data-stu-id="8d801-p109">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```
<span data-ttu-id="8d801-151">Когда вы будете готовы закрыть все окна Windows PowerShell, выполните следующую команду, чтобы удалить активных сеансов для Скайп для бизнеса в Интернет, Exchange Online, SharePoint Online и безопасность &amp; центре соответствия требованиям:</span><span class="sxs-lookup"><span data-stu-id="8d801-151">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a><span data-ttu-id="8d801-152">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="8d801-152">New to Office 365?</span></span>
<span data-ttu-id="8d801-153"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="8d801-153"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="8d801-154">См. также</span><span class="sxs-lookup"><span data-stu-id="8d801-154">See also</span></span>

- [<span data-ttu-id="8d801-155">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="8d801-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="8d801-156">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d801-156">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="8d801-157">Управление SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d801-157">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="8d801-158">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d801-158">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="8d801-159">Использование Windows PowerShell для создания отчетов в Office 365</span><span class="sxs-lookup"><span data-stu-id="8d801-159">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
