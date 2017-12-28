---
title: "Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)"
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
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "Сводка. Использование удаленного сеанса Windows PowerShell для подключения к Exchange Online с помощью параметра DelegatedOrg."
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Подключение к клиентам Exchange Online с помощью удаленного сеанса Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)

 **Сводка.** Используйте удаленный сеанс Windows PowerShell для подключения к Exchange Online с помощью параметра _DelegatedOrg_.
  
Удаленный сеанс Windows PowerShell позволяет управлять параметрами Exchange Online из командной строки. С помощью Windows PowerShell на локальном компьютере можно создать удаленный сеанс с Exchange Online. Это трехэтапный процесс, в ходе которого вы вводите свои учетные данные Exchange Online, задаете необходимые параметры подключения, а затем импортируете командлеты Exchange Online в локальный сеанс Windows PowerShell, чтобы их можно было использовать.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы?

- Предполагаемое время для завершения: 5 минут.
    
- Ниже приведены версии Windows, которые можно использовать.
    
  - Windows 10
    
  - Windows 8.1 или Windows 8
    
  - Windows Server 2012 R2 или Windows Server 2012
    
  - Windows 7 с пакетом обновления 1 (SP1)*
    
  - Windows Server 2008 R2 с пакетом обновления 1 (SP1)*
    
    * Вам потребуется установить .NET Framework 4.5.1 или .NET Framework 4.5, а затем  Windows Management Framework 4.0 или Windows Management Framework 3.0. Дополнительные сведения см. в указанных ниже ресурсах.
    
  - [Установка .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- Сведения о сочетаниях клавиш, которые можно использовать в процедурах из этой статьи, см. в статье [Сочетания клавиш в Центре администрирования Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).
    
## 

> [!IMPORTANT]
> Эта процедура предназначена только дляпартнеров службы разрешений делегированного доступа (DAP). Если вы не являетесь партнером DAP, не используйте эту процедуру. 
  
Партнеры DAP являются партнерами синдикации и поставщиков облачных решений (CSP). Они часто являются поставщиками сети или телекоммуникационных услуг в других компаниях. Они включают подписки в услуги для своих клиентов. Они владеют партнерскими правами, что автоматически предоставляет разрешение на администрирование от имени (AOBO) их клиентамOffice 365:, так что они имеют право на администрирование всех своих клиентов и создание отчетов о них.
  
## <a name="connect-to-exchange-online"></a>Подключение к Exchange Online

1. На локальном компьютере откройте Windows PowerShell и запустите следующую команду:
    
  ```
  $UserCredential = Get-Credential
  ```

    В диалоговом окне **Запрос учетных данных Windows PowerShell** введите имя пользователя и пароль администратора DAP, а затем нажмите кнопку **ОК**.
    
2. Выполните следующую команду, заменив  _<customer tenant domain name>_ именем клиентского домена, к которому нужно подключиться.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    Ключевой этап этой команды  указание пользователя, отчетные данные о котором нужно получить. Это делается в параметре  _ConnectionURI_, где указывается полное имя исходного домена как значение параметра  _DelegatedOrg_. Это указывает конечную точку удаленного Windows PowerShell удаленной консоли Windows PowerShell для Exchange Online PowerShell, к которой нужно подключиться. Консоль Windows PowerShell должна подключаться к службе отчетов Office 365: в контексте определенного пользователя при каждом запуске. После того как указывается пользователь, запускаются все указанные команды в контексте этого пользователя. Это позволяет партнеру получать доступ ко всем доступным отчетам для этого пользователя.
    
3. Выполните следующую команду:
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> В одной учетной записи можно одновременно запускать до трех сеансов. По завершении настройки отключите удаленный сеанс Windows PowerShell. Если закрыть окно Windows PowerShell, не выполнив отключение сеанса, то можно исчерпать лимит доступных сеансов удаленной среды Windows PowerShell. К тому же, придется дождаться завершения сеанса. Чтобы отключить удаленный сеанс Windows PowerShell, выполните приведенную ниже команду. >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>Как проверить, что все получилось?

После шага 3 командлеты Exchange Online импортируются в локальный сеанс Windows PowerShell, на что указывает индикатор выполнения. Если при этом не возникают ошибки, подключение установлено. Чтобы выполнить быструю проверку, запустите командлет Exchange Online, например **Get-Mailbox**, и просмотрите результаты его выполнения.
  
Если возникают ошибки, просмотрите список возможных причин:
  
- Распространенная проблема — неправильный пароль. Еще раз повторите три описанные выше действия, уделив особое внимание действию 1 — вводу имени пользователя и пароля.
    
- Для предотвращения атак типа "отказ в обслуживании" (DoS) можно открыть не более трех подключений оболочки Windows PowerShell к организации Exchange Online.
    
- Windows PowerShell необходимо настроить для запуска сценариев. Эта настройка выполняется на компьютере только однажды, а не каждый раз при подключении. Чтобы включить выполнение подписанных сценариев в Windows PowerShell, выполните следующую команду в окне Windows PowerShell с повышенными привилегиями (окно Windows PowerShell, которое открывается с помощью параметра **Запуск от имени администратора**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- Для учетной записи, которую вы используете для подключения к Exchange Online, необходимо включить доступ к удаленной оболочке Windows PowerShell. Дополнительные сведения см. в статье [Управление удаленным доступом к PowerShell в Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- Между клиентским компьютером и службой Exchange Online должен быть открыт порт TCP-порт 80. Вполне вероятно, что он уже открыт, то в этом следует убедиться, если в вашей организации действует политика ограниченного доступа к Интернету.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Вызывайте командлет напрямую с помощью команды Invoke-Command

Импорт удаленного сеанса Windows PowerShell может занимать много времени, поскольку в нем используются все командлеты Exchange Online. Это может быть проблемой при пакетной обработке, например если создаются отчеты или выполняется пакетное изменение для разных клиентов. Вместо того чтобы использовать **Import-PSSession**, вы можете вызывать нужные командлеты напрямую с помощью инструкции **Invoke-Command**. Например, чтобы вызвать командлет **get-mailbox**, вставьте этот код вместо `Import-PSSession $Session`.
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Дополнительные командлеты для отчетов

В этом разделе используются командлеты Windows PowerShell. Дополнительные сведения об этих командлетах см. в следующих статьях.
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618);
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621);
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619);
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620);
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

