---
title: "Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: 'Summary: Connect Windows PowerShell to all Office 365 services in a single Windows PowerShell window.'
ms.openlocfilehash: 2dccfc73b016cbe97436c822432331ee30ba4bcd
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell

 **Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.
  
When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:
  
![Пять консолей Windows PowerShell, работающих одновременно](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.
  
## <a name="before-you-begin"></a>Перед началом работы
<a name="BeforeYouBegin"> </a>

Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:
  
- The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.
    
- Ниже приведены 64-разрядные версии Windows, которые можно использовать.
    
  - Windows 10
    
  - Windows 8.1 или Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 или Windows Server 2012
    
  - Windows 7 с пакетом обновления 1 (SP1)*
    
  - Windows Server 2008 R2 с пакетом обновления 1 (SP1)*
    
    * You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.
    
- You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:
    
  - [Microsoft Online Service Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [Windows Azure Active Directory Module for Windows PowerShell (64-bit version)](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [Skype for Business Online, Windows PowerShell Module](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a>Краткая версия (инструкции без пояснений)
<a name="ShortVersion"> </a>

В этом разделе описываются шаги подключения без подробных пояснений. Если у вас возникнут вопросы или вам потребуются дополнительные сведения, можно обратиться к остальным разделам статьи. Указанные здесь номера шагов соответствуют шагам в остальных разделах данной статьи.
  
1. Open Windows PowerShell as an administrator (use **Run as administrator**).
    
2. Run this command, and enter your Office 365 work or school account credentials.
    
  ```
  $credential = Get-Credential
  ```

3. Run these commands to connect to Office 365.
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Run these commands to connect to Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. Run these commands to connect to the Security &amp; Compliance Center.
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.
  
Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.
  
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

When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Подробная версия (инструкции с подробными пояснениями)
<a name="LongVersion"> </a>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a>Шаг 1. Запуск Windows PowerShell от имени администратора
<a name="Step1"> </a>

If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:
  
1. Use any of these methods to find the shortcut for **Windows PowerShell**:
    
  - On the Start screen, click an empty area, and type Windows PowerShell.
    
  - On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.
    
  - On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.
    
2. In the results, right-click **Windows PowerShell**, and select **Run as administrator**.
    
3. If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.
    
If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:
  
1. On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.
    
2. If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.
    
You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a>Этап 2. Создание объекта учетных данных Windows PowerShell
<a name="Step2"> </a>

The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.
  
```
$credential = Get-Credential
```

> [!NOTE]
>  `$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.
  
Windows PowerShell will then display a dialog box that looks like this.
  
![Диалоговое окно запроса блокировки учетных данных.](images/o365_powershell_empty_credentials_box.png)
  
Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:
  
![Диалоговое окно запроса полных учетных данных.](images/o365_powershell_completed_credentials_box.png)
  
Обратите внимание на то, что, как часто в случае, вы не увидите запрос на подтверждение, что был создан объект учетных данных. (Windows PowerShell обычно о том, когда вещей ошибок, но не всегда сообщает, когда вещей перейдите вправо.) Если вы хотите убедиться, что был создан объект учетные данные, введите следующую команду в Windows PowerShell и нажмите клавишу ВВОД.
  
```
$credential
```

На экране должно отобразиться что-то вроде этого:
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

— Это следует помнить, что командлет [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) только создает объект учетных данных; не выполнить проверку подлинности, и в противном случае проверьте правильность имени пользователя и пароль. Например предположим, что вы ввели имя пользователя, kenmyer@litwareinc.onmicrosoft.com. Если вы сделаете это, **Get-Credential** будет создан объект учетные данные, используя это имя пользователя и без проверки на предмет, — это фактически допустимое имя пользователя. Не будут знать ли объект действительно допустимые учетные данные были созданы до фактически использовать этот объект подключения к службам Office 365.
  
### <a name="step-3-connect-to-office-365"></a>Действие 3. Подключение к Office 365
<a name="Step3"> </a>

We'll start by connecting to Office 365 itself. 
  
The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.
  
```
Import-Module MsOnline
```

Чтобы проверить, успешно ли импортирован модуль, выполните следующую команду:
  
```
Get-Module
```

Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.
  
Если вы видите `MSOnline` в списке, это означает, что все выполнено согласно плану.
  
С помощью создания объекта учетные данные (см [Шаг 2: создание объекта учетных данных Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)), а также с `MsOnline` модулем, мы можно теперь подключение к Office 365 с помощью командлета [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) и следующую команду.
  
```
Connect-MsolService -Credential $credential
```

Обратите внимание, что все, что необходимо указать — это объект учетные данные ( `$credential`). На основе этих учетных данных, Office 365 будет автоматически подключаются к правильный домен. Необходимо указать имя домена, при запуске **Connect-MsolService**.
  
To verify that you really  *are*  connected to Office 365, run this command.
  
```
Get-MsolDomain
```

В ответ вы должны получить что-то вроде этого:
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a>Действие 4. Подключение к SharePoint Online
<a name="Step4"> </a>

Import the SharePoint Online module with the following command:
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

Переключатель _DisableNameChecking_ подавляет появление этого предупреждения.
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

Чтобы подключиться к SharePoint Online, необходимо указать следующая информация: свои учетные данные и URL-адрес веб-узла администрирования SharePoint Online. Часть учетные данные прост: мы уже хранятся, указанному в переменной `$credential` (видеть [Шаг 2: создание объекта учетных данных Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). Как для URL-адрес сайта администрирования, простой определить, а также. Предположим, что имя домена Office 365 — это `litwareinc.onmicrosoft.com`.
  
Чтобы определить URL-адрес сайта администрирования, выполните перечисленные ниже действия.
  
1. Start by using the prefix  `https://`.
    
2. Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.
    
3. Add a hyphen (-) followed by  `admin.sharepoint.com`.
    
Другими словами:
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
После создания URL-адрес, затем можно использовать этот URL-адрес и объект учетных данных для подключения к SharePoint Online. Просто вызовите командлет [Connect-sposervice открывает](https://go.microsoft.com/fwlink/p/?LinkId=532436) , используя команду, аналогичную этой.
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

Чтобы убедиться в том, что выполнено подключение, выполните следующую команду в Windows PowerShell.
  
```
Get-SPOSite
```

Вы должны получить список всех сайтов SharePoint Online. Ниже приведен пример:
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

Office 365 команды (Следуйте описанной в [Шаг 3: подключение к Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) будет по-прежнему работали. (Попробуйте выполнить **Такую**и посмотрите сами.) Это означает, что теперь можно управлять Office 365 и SharePoint Online из одного экземпляра Windows PowerShell.
  
### <a name="step-5-connect-to-skype-for-business-online"></a>Шаг 5. Подключение к Skype для бизнеса Online
<a name="Step5"> </a>

Подключение к Скайп для бизнеса в Интернет (и в Exchange Online и безопасность &amp; центре соответствия требованиям), отличается от подключение к Office 365 или в SharePoint Online. Вот так как Скайп по командлетам Business Online и Exchange Online не получите установленный на компьютере, как командлеты SharePoint Online и Office 365. Вместо этого каждый раз, когда входа, соответствующие командлеты, временно копируются на своем компьютере. При выйти из этих командлетов затем удаляются со своего компьютера.
  
Чтобы подключиться к Скайп для бизнеса в Интернет, необходимо импортировать Скайп для бизнеса в Интернет модуля. Для этого выполните эту команду.
  
```
Import-Module SkypeOnlineConnector
```

При первом запуске может появиться следующее сообщение об ошибке, которое можно смело игнорировать:
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

После импорта модуля выполните следующую команду:
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

Мы создали удаленного сеанса PowerShell. В этом случае это означает, что мы было установлено подключение к экземпляру ядра Windows PowerShell на одном из серверов Office 365. 
  
Несмотря на то, что внесенные подключение к Office 365 мы еще не загружен, сценарии, командлеты и другие элементы, необходимые для управления Скайп для бизнеса в Интернет. Для этого необходимо, выполните следующую команду.
  
```
Import-PSSession $sfboSession
```

When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.
  
![Строка хода выполнения Lync Online.](images/o365_powershell_lync_progress_bar.png)
  
Когда индикатор выполнения исчезнет, будут выведены показанные ниже результаты.
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a>Шаг 6. Подключение к Exchange Online
<a name="Step6"> </a>

Выполните эту команду, которая создает удаленного сеанса Windows PowerShell с Exchange Online.
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> Почему — команда для подключения к Exchange Online сложнее, чем команду для подключения к Скайп для бизнеса в Интернет? Технически, это не: обе команды выполните те же самые функции. Тем не менее, Скайп для бизнеса в Интернет команды создать собственный командлет — **New-CsOnlineSession** —, скрывает некоторые параметры (например, _Проверка подлинности_ и _AllowRedirection_), используемые при подключении к Exchange Online. Устраняет необходимость ввести эти данные самостоятельно, параметры _проверки подлинности_ и _AllowRedirection_ эффективно встроены командлет **New-CsOnlineSession** . Необходимо ввести эти параметры при подключении к Exchange Online, так как Exchange Online с помощью командлета [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) standard для подключения к Office 365. Недостаток состоит в том, что у вас есть немного больше ввода для этого. Преимущество заключается в том, что не нужно загрузить и установить модуль Exchange Online.
  
Все, что вам потребуется выполнить теперь — импортировать этот сеанс удаленного так же, как выполнялись с Скайп для бизнеса в Интернет.
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

На экране должно отобразиться что-то вроде этого:
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

Теперь попробуйте выполнить следующую команду:
  
```
Get-AcceptedDomain
```

In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a>Step 7: Connect to the Security &amp; Compliance Center
<a name="Step7"> </a>

The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).
  
Инструкции по подключения для системы безопасности &amp; центре соответствия требованиям очень похожи на для Exchange Online, но с добавлены версия, который вы увидите позже.
  
Выполните эту команду, когда создается удаленный сеанс PowerShell с безопасностью &amp; центре соответствия требованиям.
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

Затем выполните следующую команду:
  
```
Import-PSSession $ccSession -Prefix cc
```

Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.
  
Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.
  
Что произойдет, если при попытке импорта два сеанса, содержащих командлеты с тем же именем? Они встречаются. Вы получите большой предупреждение, что, `WARNING: Proxy creation has been skipped for the following command:` за которым следует список конфликтующие командлеты, которые не могут быть импортированы. Конечный результат? **Get-RoleGroup** можно запустить в Exchange Online, так как вы сначала подключена, но не может запустить **Get-RoleGroup** в системы &amp; центра обработки соответствия требованиям, так как вы последнее существует подключенных и конфликтующие командлеты отказано для импорта.
  
Это самый простой способ решения этой проблемы необходимо добавить префикс произвольный текст для импортированных безопасности &amp; командлеты центре соответствия требованиям. Мы использовали, с помощью параметра _префикс_ со значением «копия» на командлет **Import-PSSession** . Что еще, этого для нас? Ее использованием отпала конфликты с помощью (немного) изменения в безопасности &amp; имена центре соответствия требованиям для данного сеанса. Все импортированные безопасности &amp; центре соответствия требованиям командлеты теперь начинаются с «копия» в существительных часть имени командлета (справа от «-»). Например, командлет **Get-RoleGroup** спорными становится **Get-ccRoleGroup** для системы безопасности &amp; центре соответствия требованиям, чтобы она не конфликтовала с **Get-RoleGroup** для Exchange Online.
  
Недостатки.  *Все*  Безопасность &amp; центре соответствия требованиям имена получают префикс «копия» — даже уникальные командлеты, оно не требуется. Например **Get-ComplianceSearch** становится **Get-ccComplianceSearch** , даже если нет командлет не в Exchange Online. Это немного области, но не плохо во время рассмотрения преимуществами управление всех служб Office 365 в одном сеансе Windows PowerShell. Не забудьте добавить «копия» имена для всех процедур, описанных в системы &amp; центре соответствия требованиям.
  
Если все сделано правильно, на экране появится следующее сообщение:
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

Now you are free to manage all Office 365 services in a single Windows PowerShell session.
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a>Шаг 8. Корректное завершение сеансов PowerShell
<a name="Step8"> </a>

Если вы только что закрыть окно Windows PowerShell, вашей Скайп для бизнеса в Интернет подключение к удаленному остается активным для следующего 15 минут. Так как Скайп для бизнеса в Интернет ограничивает количество одновременных подключений, имеют открыть любой одному или любой один домен, который может быть проблема. С помощью Скайп для бизнеса в Интернет отдельных администратор может иметь, не более трех подключений за один раз и в домене может быть не более девяти открытых подключений. Если вход на портал Скайп для бизнеса в Интернет и выйти из режима без закрытия сеанса должным образом, сеанс остается открытой для следующего 15 минут. В результате это одно подключение меньшего числа доступных вам или другим администраторам в вашем домене.
  
Вместо этого, давайте закрыть удаленных сеансов для Скайп для бизнеса в Интернет, Exchange Online и безопасность &amp; соответствия центрирования соответствующим образом. Сначала, выполните следующую команду.
  
```
Get-PSSession
```

The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).
  
![Консоль Windows PowerShell без удаленных сеансов](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`
  
If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.
  
To close the SharePoint Online session, type this command.
  
```
Disconnect-SPOService
```

If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

You can't retrieve site information because you're no longer connected to SharePoint Online.
  
As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.
  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?
<a name="LongVersion"> </a>

||
|:-----|
|![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning. |
   
## <a name="see-also"></a>См. также

#### 

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Управление SharePoint Online с помощью Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
  
[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Использование Windows PowerShell для создания отчетов в Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

