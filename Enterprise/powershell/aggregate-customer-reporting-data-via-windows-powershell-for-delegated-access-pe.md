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
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>Сбор отчетных данных о пользователях с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)

 **Сводка:** С помощью Windows PowerShell для Office 365 для получения отчетов на все клиенты клиента и объединения данных в одном месте.
  
По умолчанию Windows PowerShell для Office 365: не содержит встроенной функции сбора отчетных данных из нескольких пользовательских клиентов. Тем не менее, вы можете использовать этот пример сценария Windows PowerShell для Office 365:, чтобы обойти все пользовательские клиенты и получить единый отчет обо всех пользователях, а затем собрать отчетные данные в одном хранилище. В результате получится один отчет обо всех пользовательских клиентах. 
  
Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP). Они часто бывают поставщиками услуг, связанных с сетью или телекоммуникацией, в других компаниях. Они внесли подписки на Office 365: в пакет своих услуг. Продавая подписки на Office 365:, они автоматически получают разрешения на администрирование от чьего-либо имени (AOBO) дляобласти клиентов пользователя, что позволяет им администрировать эти области и создавать отчеты.
## <a name="before-you-begin"></a>Приступая к работе

Чтобы использовать этот сценарий, замените значения указанных ниже переменных своими значениями.
  
- **$UserName**  это имя администратора партнера. Эти учетные данные будут использоваться для подключения ко всем пользовательским клиентам.
    
- **$OutputFile**  это файл значений с разделителями-запятыми, в котором будут собраны отчетные данные.
    
- **$ErrorFile**  это текстовый файл журнала для ошибок.
    
- **$ScriptBlock**  этот пример сценария использует команду **Get-MailboxActivityReport** и параметры (например, даты начала и окончания), позволяющие вам приступить к работе. Если вам потребуются другие отчеты, укажите нужные имя отчета и параметры в команде **Get-MailboxActivityReport**.
    
- Откройте удаленный сеанс Windows PowerShell с Exchange Online, следуя указаниям из статьи [Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>Используйте Windows PowerShell, чтобы собрать отчеты о пользовательских клиентах в одном хранилище

1. Скопируйте и вставьте сценарий в Блокнот.
    
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

2. Сохраните сценарий в файле GetMailboxActivityReport.ps1 в расположении, которое вам будет легко найти. Например, этот файл сохранен в папке C:\\O365 Scripts. 
    
3. Запустите сценарий в удаленном сеансе Windows PowerShell, соблюдая синтаксис.
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

Пример сценария помещает собранный отчет в файл ReportOutput.csv.
  
## <a name="see-also"></a>See also

#### 

[Справка для партнеров](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Веб-служба отчетов Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Командлеты отчетов Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)

