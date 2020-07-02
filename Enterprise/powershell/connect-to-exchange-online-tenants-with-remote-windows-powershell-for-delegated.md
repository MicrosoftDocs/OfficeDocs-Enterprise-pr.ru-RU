---
title: Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: Сводка. Использование удаленного сеанса Windows PowerShell для подключения к Exchange Online с помощью значения DelegatedOrg.
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997375"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="75f62-103">Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="75f62-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75f62-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span><span class="sxs-lookup"><span data-stu-id="75f62-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span></span> <span data-ttu-id="75f62-105">If you aren't a DAP partner, don't use the procedures in this topic.</span><span class="sxs-lookup"><span data-stu-id="75f62-105">If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="75f62-106">Партнеры DAP являются партнерами синдикации и поставщиков облачных решений (CSP).</span><span class="sxs-lookup"><span data-stu-id="75f62-106">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="75f62-107">Они часто являются поставщиками сети или телекоммуникационных услуг в других компаниях.</span><span class="sxs-lookup"><span data-stu-id="75f62-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="75f62-108">Они включают подписки в услуги для своих клиентов.</span><span class="sxs-lookup"><span data-stu-id="75f62-108">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="75f62-109">Они владеют партнерской арендой, которая автоматически получает права администратора от имени (АОБО) для пользователей Microsoft 365, чтобы они могли администрировать и предоставлять отчеты для всех клиентов клиенты.</span><span class="sxs-lookup"><span data-stu-id="75f62-109">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="75f62-110">Партнеры по настройке доступа к данным могут использовать Exchange Online PowerShell для управления параметрами клиента Exchange Online и получения отчетов Microsoft 365 из командной строки.</span><span class="sxs-lookup"><span data-stu-id="75f62-110">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="75f62-111">С помощью Windows PowerShell на локальном компьютере можно создать удаленный сеанс PowerShell с Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="75f62-111">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="75f62-112">Это простой процесс в три этапа, в котором вы вводите свои учетные данные, предоставляете необходимые параметры подключения, а затем импортируете командлеты Exchange Online в локальный сеанс Windows PowerShell, чтобы их можно было использовать.</span><span class="sxs-lookup"><span data-stu-id="75f62-112">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="75f62-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75f62-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span></span> <span data-ttu-id="75f62-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span><span class="sxs-lookup"><span data-stu-id="75f62-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="75f62-115">Что нужно знать перед началом работы</span><span class="sxs-lookup"><span data-stu-id="75f62-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="75f62-116">Предполагаемое время для завершения: 5 минут.</span><span class="sxs-lookup"><span data-stu-id="75f62-116">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="75f62-117">Ниже приведены версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="75f62-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="75f62-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="75f62-118">Windows 10</span></span>

  - <span data-ttu-id="75f62-119">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="75f62-119">Windows 8.1</span></span>

  - <span data-ttu-id="75f62-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="75f62-120">Windows Server 2016</span></span>

  - <span data-ttu-id="75f62-121">Windows Server 2012 или Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="75f62-121">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="75f62-122">Windows 7 с пакетом обновления 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="75f62-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="75f62-123">Windows Server 2008 R2 с пакетом обновления 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="75f62-123">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="75f62-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span><span class="sxs-lookup"><span data-stu-id="75f62-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span></span> <span data-ttu-id="75f62-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span><span class="sxs-lookup"><span data-stu-id="75f62-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="75f62-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span><span class="sxs-lookup"><span data-stu-id="75f62-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span></span> <span data-ttu-id="75f62-127">You'll get the following error when you try to connect:</span><span class="sxs-lookup"><span data-stu-id="75f62-127">You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="75f62-128">Чтобы требовать подпись надежного издателя для всех сценариев PowerShell, загружаемых из Интернета, выполните следующую команду в окне Windows PowerShell с повышенными привилегиями (окно Windows PowerShell, которое открывается с помощью параметра **Запуск от имени администратора**).</span><span class="sxs-lookup"><span data-stu-id="75f62-128">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="75f62-129">Достаточно настроить этот параметр один раз, и вам не придется делать это при каждом подключении.</span><span class="sxs-lookup"><span data-stu-id="75f62-129">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="75f62-130">Сведения о сочетаниях клавиш, которые можно использовать в процедурах из этой статьи, см. в статье [Сочетания клавиш в Центре администрирования Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="75f62-130">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="75f62-131">Подключение к Exchange Online для организаций пользователей</span><span class="sxs-lookup"><span data-stu-id="75f62-131">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="75f62-132">На локальном компьютере откройте Windows PowerShell и запустите следующую команду.</span><span class="sxs-lookup"><span data-stu-id="75f62-132">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="75f62-133">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите имя пользователя и пароль администратора DAP, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="75f62-133">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="75f62-134">Замените _\<customer tenant domain name\>_ именем домена клиента, к которому вы хотите подключиться, и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="75f62-134">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="75f62-135">Ключевой этап этой команды  указание пользователя, отчетные данные о котором нужно получить.</span><span class="sxs-lookup"><span data-stu-id="75f62-135">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="75f62-136">Это можно сделать в параметре _ConnectionURI_ , где указать полное доменное имя начального доменного имени в качестве значения `?DelegatedOrg=` .</span><span class="sxs-lookup"><span data-stu-id="75f62-136">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="75f62-137">Это значение указывает правильную конечную точку Exchange Online PowerShell для подключения.</span><span class="sxs-lookup"><span data-stu-id="75f62-137">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="75f62-138">Удаленная оболочка PowerShell должна подключаться к Microsoft 365 Reports в контексте определенного клиента при каждом запуске отчета.</span><span class="sxs-lookup"><span data-stu-id="75f62-138">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="75f62-139">После подключения к Exchange Online PowerShell все последующие команды выполняются в контексте клиента, который предоставляет доступ ко всем доступным отчетам для клиента.</span><span class="sxs-lookup"><span data-stu-id="75f62-139">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="75f62-140">Выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="75f62-140">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="75f62-141">There's a limit of three simultaneous sessions that can run under one account.</span><span class="sxs-lookup"><span data-stu-id="75f62-141">There's a limit of three simultaneous sessions that can run under one account.</span></span> <span data-ttu-id="75f62-142">Be sure to disconnect the remote PowerShell session when you're finished.</span><span class="sxs-lookup"><span data-stu-id="75f62-142">Be sure to disconnect the remote PowerShell session when you're finished.</span></span> <span data-ttu-id="75f62-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span><span class="sxs-lookup"><span data-stu-id="75f62-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span></span> <span data-ttu-id="75f62-144">To disconnect the remote PowerShell session, run the following command:</span><span class="sxs-lookup"><span data-stu-id="75f62-144">To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="75f62-145">Как проверить, что все получилось?</span><span class="sxs-lookup"><span data-stu-id="75f62-145">How do you know this worked?</span></span>

<span data-ttu-id="75f62-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span><span class="sxs-lookup"><span data-stu-id="75f62-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span></span> <span data-ttu-id="75f62-147">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="75f62-147">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="75f62-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span><span class="sxs-lookup"><span data-stu-id="75f62-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="75f62-149">Если возникают ошибки, просмотрите список возможных причин ниже.</span><span class="sxs-lookup"><span data-stu-id="75f62-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="75f62-150">A common problem is an incorrect password.</span><span class="sxs-lookup"><span data-stu-id="75f62-150">A common problem is an incorrect password.</span></span> <span data-ttu-id="75f62-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span><span class="sxs-lookup"><span data-stu-id="75f62-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="75f62-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75f62-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span></span> <span data-ttu-id="75f62-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="75f62-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="75f62-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="75f62-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span></span> <span data-ttu-id="75f62-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span><span class="sxs-lookup"><span data-stu-id="75f62-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="75f62-156">Вызов командлета напрямую с помощью команды Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="75f62-156">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="75f62-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span><span class="sxs-lookup"><span data-stu-id="75f62-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span></span> <span data-ttu-id="75f62-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span><span class="sxs-lookup"><span data-stu-id="75f62-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span></span> <span data-ttu-id="75f62-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="75f62-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span></span> <span data-ttu-id="75f62-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span><span class="sxs-lookup"><span data-stu-id="75f62-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="75f62-161">Дополнительные командлеты для отчетов</span><span class="sxs-lookup"><span data-stu-id="75f62-161">More reporting cmdlets</span></span>

<span data-ttu-id="75f62-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span><span class="sxs-lookup"><span data-stu-id="75f62-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span></span> <span data-ttu-id="75f62-163">For more information about these cmdlets, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="75f62-163">For more information about these cmdlets, see the following topics:</span></span>
  
- <span data-ttu-id="75f62-164">[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618);</span><span class="sxs-lookup"><span data-stu-id="75f62-164">[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)</span></span>
    
- <span data-ttu-id="75f62-165">[New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621);</span><span class="sxs-lookup"><span data-stu-id="75f62-165">[New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)</span></span>
    
- <span data-ttu-id="75f62-166">[Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619);</span><span class="sxs-lookup"><span data-stu-id="75f62-166">[Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)</span></span>
    
- <span data-ttu-id="75f62-167">[Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620);</span><span class="sxs-lookup"><span data-stu-id="75f62-167">[Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)</span></span>
    
- <span data-ttu-id="75f62-168">[Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623).</span><span class="sxs-lookup"><span data-stu-id="75f62-168">[Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)</span></span>
    

