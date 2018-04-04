---
title: Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: Сводка. Использование удаленного сеанса Windows PowerShell для подключения к Exchange Online с помощью параметра DelegatedOrg.
ms.openlocfilehash: d8cbb6640419ba2f1de868ae88b0a273c3f71ae7
ms.sourcegitcommit: f3f81d2c2e8290948d93f3f787a679c804840256
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="a4dd6-103">Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="a4dd6-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="a4dd6-104">**Сводка.** Используйте удаленный сеанс Windows PowerShell для подключения к Exchange Online с помощью параметра _DelegatedOrg_.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="a4dd6-p101">Удаленный сеанс Windows PowerShell позволяет управлять параметрами Exchange Online из командной строки. С помощью Windows PowerShell на локальном компьютере можно создать удаленный сеанс с Exchange Online. Это трехэтапный процесс, в ходе которого вы вводите свои учетные данные Exchange Online, задаете необходимые параметры подключения, а затем импортируете командлеты Exchange Online в локальный сеанс Windows PowerShell, чтобы их можно было использовать.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="a4dd6-108">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="a4dd6-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="a4dd6-109">Предполагаемое время для завершения: 5 минут.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="a4dd6-110">Ниже приведены версии Windows, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="a4dd6-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a4dd6-111">Windows 10</span></span>
    
  - <span data-ttu-id="a4dd6-112">Windows 8.1 или Windows 8</span><span class="sxs-lookup"><span data-stu-id="a4dd6-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="a4dd6-113">Windows Server 2012 R2 или Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a4dd6-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="a4dd6-114">Windows 7 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="a4dd6-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="a4dd6-115">Windows Server 2008 R2 с пакетом обновления 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="a4dd6-115">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="a4dd6-p102">\* Необходимо установить .NET Framework 4.5.1 или .NET Framework 4.5, а затем Windows Management Framework 4.0 или Windows Management Framework 3.0. Дополнительные сведения см. в указанных ниже ресурсах.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p102">\*You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
    - [<span data-ttu-id="a4dd6-118">Установка .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4dd6-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
    - <span data-ttu-id="a4dd6-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="a4dd6-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="a4dd6-120">Сведения о сочетаниях клавиш, которые можно использовать в процедурах из этой статьи, см. в статье [Сочетания клавиш в Центре администрирования Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="a4dd6-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="a4dd6-p103">Эта процедура предназначена только дляпартнеров службы разрешений делегированного доступа (DAP). Если вы не являетесь партнером DAP, не используйте эту процедуру.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="a4dd6-p104">Партнеры DAP являются партнерами синдикации и поставщиков облачных решений (CSP). Они часто являются поставщиками сети или телекоммуникационных услуг в других компаниях. Они включают подписки в услуги для своих клиентов. Они владеют партнерскими правами, что автоматически предоставляет разрешение на администрирование от имени (AOBO) их клиентамOffice 365:, так что они имеют право на администрирование всех своих клиентов и создание отчетов о них.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="a4dd6-127">Подключение к Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a4dd6-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="a4dd6-128">На локальном компьютере откройте Windows PowerShell и запустите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="a4dd6-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="a4dd6-129">В диалоговом окне **Запрос учетных данных Windows PowerShell** введите имя пользователя и пароль администратора DAP, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="a4dd6-130">Выполните следующую команду, заменив  _<customer tenant domain name>_ именем клиентского домена, к которому нужно подключиться.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="a4dd6-p105">Ключевой этап этой команды  указание пользователя, отчетные данные о котором нужно получить. Это делается в параметре  _ConnectionURI_, где указывается полное имя исходного домена как значение параметра  _DelegatedOrg_. Это указывает конечную точку удаленного Windows PowerShell удаленной консоли Windows PowerShell для Exchange Online PowerShell, к которой нужно подключиться. Консоль Windows PowerShell должна подключаться к службе отчетов Office 365: в контексте определенного пользователя при каждом запуске. После того как указывается пользователь, запускаются все указанные команды в контексте этого пользователя. Это позволяет партнеру получать доступ ко всем доступным отчетам для этого пользователя.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="a4dd6-137">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="a4dd6-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="a4dd6-p106">В одной учетной записи можно одновременно запускать до трех сеансов. По завершении настройки отключите удаленный сеанс Windows PowerShell. Если закрыть окно Windows PowerShell, не выполнив отключение сеанса, то можно исчерпать лимит доступных сеансов удаленной среды Windows PowerShell. К тому же, придется дождаться завершения сеанса. Чтобы отключить удаленный сеанс Windows PowerShell, выполните приведенную ниже команду. >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="a4dd6-142">Как проверить, что все получилось?</span><span class="sxs-lookup"><span data-stu-id="a4dd6-142">How do you know this worked?</span></span>

<span data-ttu-id="a4dd6-p107">После шага 3 командлеты Exchange Online импортируются в локальный сеанс Windows PowerShell, на что указывает индикатор выполнения. Если при этом не возникают ошибки, подключение установлено. Чтобы выполнить быструю проверку, запустите командлет Exchange Online, например **Get-Mailbox**, и просмотрите результаты его выполнения.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="a4dd6-146">Если возникают ошибки, просмотрите список возможных причин:</span><span class="sxs-lookup"><span data-stu-id="a4dd6-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="a4dd6-p108">Распространенная проблема — неправильный пароль. Еще раз повторите три описанные выше действия, уделив особое внимание действию 1 — вводу имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="a4dd6-149">Для предотвращения атак типа "отказ в обслуживании" (DoS) можно открыть не более трех подключений оболочки Windows PowerShell к организации Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="a4dd6-p109">Windows PowerShell необходимо настроить для запуска сценариев. Эта настройка выполняется на компьютере только однажды, а не каждый раз при подключении. Чтобы включить выполнение подписанных сценариев в Windows PowerShell, выполните следующую команду в окне Windows PowerShell с повышенными привилегиями (окно Windows PowerShell, которое открывается с помощью параметра **Запуск от имени администратора**).</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="a4dd6-p110">Для учетной записи, которую вы используете для подключения к Exchange Online, необходимо включить доступ к удаленной оболочке Windows PowerShell. Дополнительные сведения см. в статье [Управление удаленным доступом к PowerShell в Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="a4dd6-p111">Между клиентским компьютером и службой Exchange Online должен быть открыт порт TCP-порт 80. Вполне вероятно, что он уже открыт, то в этом следует убедиться, если в вашей организации действует политика ограниченного доступа к Интернету.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="a4dd6-157">Вызывайте командлет напрямую с помощью команды Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a4dd6-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="a4dd6-p112">Импорт удаленного сеанса Windows PowerShell может занимать много времени, поскольку в нем используются все командлеты Exchange Online. Это может быть проблемой при пакетной обработке, например если создаются отчеты или выполняется пакетное изменение для разных клиентов. Вместо того чтобы использовать **Import-PSSession**, вы можете вызывать нужные командлеты напрямую с помощью инструкции **Invoke-Command**. Например, чтобы вызвать командлет **get-mailbox**, вставьте этот код вместо `Import-PSSession $Session`.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="a4dd6-162">Дополнительные командлеты для отчетов</span><span class="sxs-lookup"><span data-stu-id="a4dd6-162">More reporting cmdlets</span></span>

<span data-ttu-id="a4dd6-p113">В этом разделе используются командлеты Windows PowerShell. Дополнительные сведения об этих командлетах см. в следующих статьях.</span><span class="sxs-lookup"><span data-stu-id="a4dd6-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- <span data-ttu-id="a4dd6-165">[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618);</span><span class="sxs-lookup"><span data-stu-id="a4dd6-165">[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)</span></span>
    
- <span data-ttu-id="a4dd6-166">[New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621);</span><span class="sxs-lookup"><span data-stu-id="a4dd6-166">[New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)</span></span>
    
- <span data-ttu-id="a4dd6-167">[Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619);</span><span class="sxs-lookup"><span data-stu-id="a4dd6-167">[Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)</span></span>
    
- <span data-ttu-id="a4dd6-168">[Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620);</span><span class="sxs-lookup"><span data-stu-id="a4dd6-168">[Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)</span></span>
    
- [<span data-ttu-id="a4dd6-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="a4dd6-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

