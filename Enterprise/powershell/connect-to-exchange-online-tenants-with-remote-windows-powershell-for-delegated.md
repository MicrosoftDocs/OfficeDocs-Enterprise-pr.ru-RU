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
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)

> [!IMPORTANT]
> The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic. 
  
Партнеры DAP являются партнерами синдикации и поставщиков облачных решений (CSP). Они часто являются поставщиками сети или телекоммуникационных услуг в других компаниях. Они включают подписки в услуги для своих клиентов. Они владеют партнерской арендой, которая автоматически получает права администратора от имени (АОБО) для пользователей Microsoft 365, чтобы они могли администрировать и предоставлять отчеты для всех клиентов клиенты.

Партнеры по настройке доступа к данным могут использовать Exchange Online PowerShell для управления параметрами клиента Exchange Online и получения отчетов Microsoft 365 из командной строки. С помощью Windows PowerShell на локальном компьютере можно создать удаленный сеанс PowerShell с Exchange Online. Это простой процесс в три этапа, в котором вы вводите свои учетные данные, предоставляете необходимые параметры подключения, а затем импортируете командлеты Exchange Online в локальный сеанс Windows PowerShell, чтобы их можно было использовать.

> [!NOTE]
> DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы

- Предполагаемое время для завершения: 5 минут.

- Ниже приведены версии Windows, которые можно использовать.
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 или Windows Server 2012 R2

  - Windows 7 с пакетом обновления 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 с пакетом обновления 1 (SP1)<sup>*</sup>

    <sup>*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  Чтобы требовать подпись надежного издателя для всех сценариев PowerShell, загружаемых из Интернета, выполните следующую команду в окне Windows PowerShell с повышенными привилегиями (окно Windows PowerShell, которое открывается с помощью параметра **Запуск от имени администратора**).

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  Достаточно настроить этот параметр один раз, и вам не придется делать это при каждом подключении.

- Сведения о сочетаниях клавиш, которые можно использовать в процедурах из этой статьи, см. в статье [Сочетания клавиш в Центре администрирования Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).

## <a name="connect-to-exchange-online-for-customer-organizations"></a>Подключение к Exchange Online для организаций пользователей

1. На локальном компьютере откройте Windows PowerShell и запустите следующую команду.
    
    ```
    $UserCredential = Get-Credential
    ```

    В диалоговом окне **Запрос учетных данных Windows PowerShell** введите имя пользователя и пароль администратора DAP, а затем нажмите кнопку **ОК**.
    
2. Замените _\<customer tenant domain name\>_ именем домена клиента, к которому вы хотите подключиться, и выполните следующую команду:
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    Ключевой этап этой команды  указание пользователя, отчетные данные о котором нужно получить. Это можно сделать в параметре _ConnectionURI_ , где указать полное доменное имя начального доменного имени в качестве значения `?DelegatedOrg=` . Это значение указывает правильную конечную точку Exchange Online PowerShell для подключения. Удаленная оболочка PowerShell должна подключаться к Microsoft 365 Reports в контексте определенного клиента при каждом запуске отчета. После подключения к Exchange Online PowerShell все последующие команды выполняются в контексте клиента, который предоставляет доступ ко всем доступным отчетам для клиента.
    
3. Выполните следующую команду.
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>Как проверить, что все получилось?

After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.
  
Если возникают ошибки, просмотрите список возможных причин ниже.
  
- A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.
    
- The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Вызов командлета напрямую с помощью команды Invoke-Command

Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Дополнительные командлеты для отчетов

The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618);
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621);
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619);
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620);
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623).
    

