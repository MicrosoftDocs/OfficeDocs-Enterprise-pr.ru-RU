---
title: "Сбор отчетных данных о пользователях с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "Сводка. Узнайте, как использовать Windows PowerShell для Office 365:, чтобы получить отчеты по всем пользовательским клиентам и собрать данные в одном хранилище."
ms.openlocfilehash: 89651971424d1b9a494335572d2654d8402ec146
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="f4cc8-103">Сбор отчетных данных о пользователях с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="f4cc8-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="f4cc8-104">**Сводка.** Получайте отчеты по всем клиентам и собирайте данные в одном месте, используя Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-104">Summary: Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="f4cc8-p101">По умолчанию Windows PowerShell для Office 365: не содержит встроенной функции сбора отчетных данных из нескольких пользовательских клиентов. Тем не менее, вы можете использовать этот пример сценария Windows PowerShell для Office 365:, чтобы обойти все пользовательские клиенты и получить единый отчет обо всех пользователях, а затем собрать отчетные данные в одном хранилище. В результате получится один отчет обо всех пользовательских клиентах.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="f4cc8-p102">Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP). Они часто бывают поставщиками услуг, связанных с сетью или телекоммуникацией, в других компаниях. Они внесли подписки на Office 365: в пакет своих услуг. Продавая подписки на Office 365:, они автоматически получают разрешения на администрирование от чьего-либо имени (AOBO) дляобласти клиентов пользователя, что позволяет им администрировать эти области и создавать отчеты.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="f4cc8-112">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="f4cc8-112">Before you begin</span></span>

<span data-ttu-id="f4cc8-113">Чтобы использовать этот сценарий, замените значения указанных ниже переменных своими значениями.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="f4cc8-p103">**$UserName**  это имя администратора партнера. Эти учетные данные будут использоваться для подключения ко всем пользовательским клиентам.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="f4cc8-116">**$OutputFile**  это файл значений с разделителями-запятыми, в котором будут собраны отчетные данные.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="f4cc8-117">**$ErrorFile**  это текстовый файл журнала для ошибок.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="f4cc8-p104">**$ScriptBlock**  этот пример сценария использует команду **Get-MailboxActivityReport** и параметры (например, даты начала и окончания), позволяющие вам приступить к работе. Если вам потребуются другие отчеты, укажите нужные имя отчета и параметры в команде **Get-MailboxActivityReport**.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="f4cc8-120">Откройте удаленный сеанс Windows PowerShell с Exchange Online, следуя указаниям из статьи [Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="f4cc8-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="f4cc8-121">Используйте Windows PowerShell, чтобы собрать отчеты о пользовательских клиентах в одном хранилище</span><span class="sxs-lookup"><span data-stu-id="f4cc8-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="f4cc8-122">Скопируйте и вставьте сценарий в Блокнот.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. <span data-ttu-id="f4cc8-p105">Сохраните сценарий в файле GetMailboxActivityReport.ps1 в расположении, которое вам будет легко найти. Например, этот файл сохранен в папке C:\\O365 Scripts.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="f4cc8-125">Запустите сценарий в удаленном сеансе Windows PowerShell, соблюдая синтаксис.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="f4cc8-126">Пример сценария помещает собранный отчет в файл ReportOutput.csv.</span><span class="sxs-lookup"><span data-stu-id="f4cc8-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f4cc8-127">См. также</span><span class="sxs-lookup"><span data-stu-id="f4cc8-127">See also</span></span>

#### 

[<span data-ttu-id="f4cc8-128">Справка для партнеров</span><span class="sxs-lookup"><span data-stu-id="f4cc8-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="f4cc8-129">Веб-служба отчетов Office 365</span><span class="sxs-lookup"><span data-stu-id="f4cc8-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="f4cc8-130">Командлеты отчетов Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f4cc8-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

