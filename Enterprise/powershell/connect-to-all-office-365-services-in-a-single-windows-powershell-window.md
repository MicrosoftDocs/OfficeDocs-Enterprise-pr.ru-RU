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
description: "Сводка: Подключение Windows PowerShell для всех служб Office 365 в одном окне Windows PowerShell."
ms.openlocfilehash: 5f97924d141afa4319c761fee86b13cb2b0705fb
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell

 **Сводка:** Вместо управление различных службах Office 365 в отдельной консоли windows PowerShell можно подключиться ко всем службам Office 365 и управлять ими из одного окна консоли.
  
При использовании PowerShell для управления Office 365, его можно установить до пяти различных Windows PowerShell открытые в то же время, соответствующий центра администрирования Office 365, SharePoint Online, Exchange Online, Скайп для бизнеса в Интернет и безопасности &amp;Центре соответствия требованиям. С помощью пяти разные способы подключения в отдельных сеансах Windows PowerShell к рабочему столу может выглядеть следующим образом:
  
![Пять консолей Windows PowerShell, работающих одновременно](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Это не является оптимальным для управления Office 365, так как не удается обмен данными между этих пяти windows для управления между службами. В этом разделе описывается, как использовать один экземпляр Windows PowerShell, из которого можно управлять Office 365, Скайп для бизнеса в Интернет, Exchange Online, SharePoint Online и безопасность &amp; центре соответствия требованиям.
  
## <a name="before-you-begin"></a>Перед началом работы
<a name="BeforeYouBegin"> </a>

Прежде чем все Office 365 можно управлять из одного экземпляра Windows PowerShell, необходимо учитывайте следующие требования:
  
- Office 365 работы или школе учетной записи, используемой для этих процедур потребностей для быть участником роли администратора Office 365. Дополнительные сведения см в [роли администраторов об Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). В этом является обязательным требованием для Office 365 PowerShell, а не обязательно для всех других служб Office 365.
    
- Ниже приведены 64-разрядные версии Windows, которые можно использовать.
    
  - Windows 10
    
  - Windows 8.1 или Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 или Windows Server 2012
    
  - Windows 7 с пакетом обновления 1 (SP1)*
    
  - Windows Server 2008 R2 с пакетом обновления 1 (SP1)*
    
    * Необходимо установить Microsoft .NET Framework 4.5. _x_ и затем либо Windows Management Framework 3.0 или Windows Management Framework 4.0. Для получения дополнительных сведений см [установки .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) и [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Необходимо использовать 64-разрядной версии Windows из-за требования к Скайп для бизнеса в Интернет в модуле и один из модулей Office 365.
    
- Требуется ли установить модули, которые необходимы для Office 365, SharePoint Online и Скайп для бизнеса в Интернет:
    
  - [Microsoft Online службы помощник по входу для ИТ-специалистов RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [Windows Azure Active Directory модуль для Windows PowerShell (64-разрядная версия)](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [Командная консоль SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [Скайп для бизнеса через Интернет, модуля Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell необходимо настроить для запуска сценариев со знаком для Скайп для бизнеса в Интернет, Exchange Online и безопасность &amp; центре соответствия требованиям. Для этого выполните следующую команду в сеансе Windows PowerShell с повышенными привилегиями (окно Windows PowerShell можно открыть, выбрав **Запуск от имени администратора**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a>Краткая версия (инструкции без пояснений)
<a name="ShortVersion"> </a>

В этом разделе описываются шаги подключения без подробных пояснений. Если у вас возникнут вопросы или вам потребуются дополнительные сведения, можно обратиться к остальным разделам статьи. Указанные здесь номера шагов соответствуют шагам в остальных разделах данной статьи.
  
1. Откройте Windows PowerShell с правами администратора ( **Запуск от имени администратора**использования).
    
2. Выполните следующую команду и введите данные Office 365 или школе учетные данные учетной записи.
    
  ```
  $credential = Get-Credential
  ```

3. Выполните следующие команды для подключения к Office 365.
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. Выполните следующие команды для подключения к SharePoint Online. Замените _ \<domainhost >_ с фактическое значение для вашего домена. Например, `litwareinc.onmicrosoft.com`, _ \<domainhost >_ значение — `litwareinc`.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Выполните следующие команды для подключения к Скайп для бизнеса в Интернет. Предупреждение о том, увеличение `WSMan NetworkDelayms` впервые ожидается значение подключения и можно пропустить.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Выполните следующие команды для подключения к Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. Выполните следующие команды для подключения к безопасности &amp; центре соответствия требованиям.
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> Текст префикса «копия» добавляется *все* безопасности &amp; имена центре соответствия требованиям, могут выполняться командлеты, который существует в Exchange Online и безопасность &amp; центре соответствия требованиям в том же сеансе Windows PowerShell. Например, **Get-RoleGroup** становится **Get-ccRoleGroup** в системы &amp; центре соответствия требованиям.
  
Ниже приведены все команды в один блок. Укажите имя вашего домена узла и затем использовать их для работы всех за один раз.
  
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

Когда вы будете готовы закрыть все окна Windows PowerShell, выполните следующую команду, чтобы удалить активных сеансов для Скайп для бизнеса в Интернет, Exchange Online, SharePoint Online и безопасность &amp; центре соответствия требованиям:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Подробная версия (инструкции с подробными пояснениями)
<a name="LongVersion"> </a>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a>Шаг 1. Запуск Windows PowerShell от имени администратора
<a name="Step1"> </a>

Если вы используете Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2 или Windows Server 2012 R2 этого сделайте следующее.
  
1. Используйте любой из следующих методов для поиска ярлыка **Windows PowerShell**:
    
  - На начальном экране щелкните пустую область и введите Windows PowerShell.
    
  - На рабочем столе или на начальном экране нажмите Windows ключевые + Q. В чудо поиска введите Windows PowerShell.
    
  - На рабочем столе или на начальном экране переместите курсор в правом верхнем углу или проведите слева от правого края экрана, чтобы отобразить чудо-кнопки. Выберите чудо поиска и введите Windows PowerShell.
    
2. В списке результатов щелкните правой кнопкой мыши **Windows PowerShell**и выберите **Запуск от имени администратора**.
    
3. Если появится диалоговое окно **Контроль учетных записей пользователей** , выберите **Да** , чтобы подтвердить запуск Windows PowerShell с использованием учетных данных администратора.
    
Если вы используете Windows 7 с пакетом обновления 1 (или Windows Server 2008 R2 SP1), это необходимо:
  
1. В меню **Пуск** выберите **Все программы** > **Стандартные** > **Windows PowerShell**. Щелкните правой кнопкой мыши **Windows PowerShell**и выберите **Запуск от имени администратора**.
    
2. Если появится диалоговое окно **Контроль учетных записей пользователей** , выберите **Да** , чтобы подтвердить запуск Windows PowerShell с использованием учетных данных администратора.
    
Windows PowerShell необходимо запустить с правами администратора. Если вы не произошло, вы собираетесь сообщение об ошибке следующего вида при попытке импортировать один из необходимых модулей.
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

Единственный способ исправить ситуацию — Windows PowerShell закройте и перезапустите его с правами администратора. Быстрый и простой способ сообщить, если вы используете Windows PowerShell с правами администратора: строке является `PS C:\Windows\System32>`, а не `PS C:\Users\YourUserName>`.

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a>Этап 2. Создание объекта учетных данных Windows PowerShell
<a name="Step2"> </a>

Объект учетных данных содержит зашифрованные способ передачи имени пользователя и пароля Windows PowerShell. Чтобы создать объект учетных данных, выполните следующую команду в Windows PowerShell.
  
```
$credential = Get-Credential
```

> [!NOTE]
>  `$credential`— это переменная, на котором будут храниться учетные данные объекта. У вас нет одно имя переменной `$credential`, но это так упрощает запомнить, к какой переменная содержит объект учетных данных. (И, важна, так как мы будем использовать эту переменную неоднократно.) Который также облегчит вам необходимо выполнить наши примеры так как всегда будет использоваться в этой статье `$credential` для представления объекта учетные данные.
  
Windows PowerShell, будет выведено диалоговое окно, которое выглядит следующим образом.
  
![Диалоговое окно запроса блокировки учетных данных.](images/o365_powershell_empty_credentials_box.png)
  
Введите данные или школе имя учетной записи в поле **имя пользователя** в формате _username@domainname_ (например, kenmyer@litwareinc.onmicrosoft.com); Введите свой пароль в поле **пароль** ; и нажмите кнопку **ОК**:
  
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

Мы начнем с помощью подключения к Office 365 самого. 
  
Первое, что нужно сделать здесь — это импорта модуля Office 365 (Microsoft Azure Active Directory модуль для Windows PowerShell). Для этого выполните эту команду в Windows PowerShell.
  
```
Import-Module MsOnline
```

Чтобы проверить, успешно ли импортирован модуль, выполните следующую команду:
  
```
Get-Module
```

Где-нибудь в списке модулей, возвращенных этой командой будет выглядеть примерно так, которая выглядит следующим образом: `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.
  
Если вы видите `MSOnline` в списке, это означает, что все выполнено согласно плану.
  
С помощью создания объекта учетные данные (см [Шаг 2: создание объекта учетных данных Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)), а также с `MsOnline` модулем, мы можно теперь подключение к Office 365 с помощью командлета [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) и следующую команду.
  
```
Connect-MsolService -Credential $credential
```

Обратите внимание, что все, что необходимо указать — это объект учетные данные ( `$credential`). На основе этих учетных данных, Office 365 будет автоматически подключаются к правильный домен. Необходимо указать имя домена, при запуске **Connect-MsolService**.
  
Чтобы проверить, которые Вы действительно *являются* подключение к Office 365, выполните следующую команду.
  
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

Импортируйте модуль SharePoint Online с помощью следующей команды:
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

Переключатель _DisableNameChecking_ подавляет появление этого предупреждения.
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

Чтобы подключиться к SharePoint Online, необходимо указать следующая информация: свои учетные данные и URL-адрес веб-узла администрирования SharePoint Online. Часть учетные данные прост: мы уже хранятся, указанному в переменной `$credential` (видеть [Шаг 2: создание объекта учетных данных Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). Как для URL-адрес сайта администрирования, простой определить, а также. Предположим, что имя домена Office 365 — это `litwareinc.onmicrosoft.com`.
  
Чтобы определить URL-адрес сайта администрирования, выполните перечисленные ниже действия.
  
1. Запуск с помощью префикса `https://`.
    
2. Добавление узла доменная часть имени домена. Например, `litwareinc.onmicrosoft.com`, — это имя узла домена `litwareinc`. Для `contoso.onmicrosoft.com`, — это имя узла домена `contoso`.
    
3. Добавьте дефис (-), за которым следует `admin.sharepoint.com`.
    
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

При импорте сеанса Windows PowerShell, вы должны увидеть индикатор хода выполнения, подобные приведенным ниже, индикатор хода выполнения, отчеты о всех Скайп для бизнеса в Интернет командлетов импортируемого на своем компьютере.
  
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

В ответ вы должны увидеть сведения об Office 365 домены, настроенные для адресов электронной почты в Exchange Online.
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a>Шаг 7: Подключение к безопасности &amp; центре соответствия требованиям
<a name="Step7"> </a>

Безопасность &amp; центре соответствия требованиям — это служба в Office 365, которая позволяет управлять функции контроля соответствия требованиям из одного расположения. Дополнительные сведения см в [центре соответствия требованиям Office 365](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).
  
Инструкции по подключения для системы безопасности &amp; центре соответствия требованиям очень похожи на для Exchange Online, но с добавлены версия, который вы увидите позже.
  
Выполните эту команду, когда создается удаленный сеанс PowerShell с безопасностью &amp; центре соответствия требованиям.
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

Затем выполните следующую команду:
  
```
Import-PSSession $ccSession -Prefix cc
```

Опять же эта команда похожа на команду для Exchange Online. Переключатель _DisableNameChecking_ не требуется, потому что существуют отсутствуют неутвержденных команды в системы &amp; центре соответствия требованиям. Но как насчет то дополнительные `-Prefix cc` параметр и значение? Добавлена версия, которую мы же говорили, о это.
  
Exchange Online и безопасность &amp; некоторые командлеты, которые имеют точно такие же имена и предоставляют те же функциональные возможности совместного использования центре соответствия требованиям. **Get-RoleGroup** является примером.
  
Что произойдет, если при попытке импорта два сеанса, содержащих командлеты с тем же именем? Они встречаются. Вы получите большой предупреждение, что, `WARNING: Proxy creation has been skipped for the following command:` за которым следует список конфликтующие командлеты, которые не могут быть импортированы. Конечный результат? **Get-RoleGroup** можно запустить в Exchange Online, так как вы сначала подключена, но не может запустить **Get-RoleGroup** в системы &amp; центра обработки соответствия требованиям, так как вы последнее существует подключенных и конфликтующие командлеты отказано для импорта.
  
Это самый простой способ решения этой проблемы необходимо добавить префикс произвольный текст для импортированных безопасности &amp; командлеты центре соответствия требованиям. Мы использовали, с помощью параметра _префикс_ со значением «копия» на командлет **Import-PSSession** . Что еще, этого для нас? Ее использованием отпала конфликты с помощью (немного) изменения в безопасности &amp; имена центре соответствия требованиям для данного сеанса. Все импортированные безопасности &amp; центре соответствия требованиям командлеты теперь начинаются с «копия» в существительных часть имени командлета (справа от «-»). Например, командлет **Get-RoleGroup** спорными становится **Get-ccRoleGroup** для системы безопасности &amp; центре соответствия требованиям, чтобы она не конфликтовала с **Get-RoleGroup** для Exchange Online.
  
Недостатки.  *Все*  Безопасность &amp; центре соответствия требованиям имена получают префикс «копия» — даже уникальные командлеты, оно не требуется. Например **Get-ComplianceSearch** становится **Get-ccComplianceSearch** , даже если нет командлет не в Exchange Online. Это немного области, но не плохо во время рассмотрения преимуществами управление всех служб Office 365 в одном сеансе Windows PowerShell. Не забудьте добавить «копия» имена для всех процедур, описанных в системы &amp; центре соответствия требованиям.
  
Если все сделано правильно, на экране появится следующее сообщение:
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

Теперь вы могут управлять всех служб Office 365 в одном сеансе Windows PowerShell.
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a>Шаг 8. Корректное завершение сеансов PowerShell
<a name="Step8"> </a>

Если вы только что закрыть окно Windows PowerShell, вашей Скайп для бизнеса в Интернет подключение к удаленному остается активным для следующего 15 минут. Так как Скайп для бизнеса в Интернет ограничивает количество одновременных подключений, имеют открыть любой одному или любой один домен, который может быть проблема. С помощью Скайп для бизнеса в Интернет отдельных администратор может иметь, не более трех подключений за один раз и в домене может быть не более девяти открытых подключений. Если вход на портал Скайп для бизнеса в Интернет и выйти из режима без закрытия сеанса должным образом, сеанс остается открытой для следующего 15 минут. В результате это одно подключение меньшего числа доступных вам или другим администраторам в вашем домене.
  
Вместо этого, давайте закрыть удаленных сеансов для Скайп для бизнеса в Интернет, Exchange Online и безопасность &amp; соответствия центрирования соответствующим образом. Сначала, выполните следующую команду.
  
```
Get-PSSession
```

Командлет [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) необходимо показать, наличие по крайней мере три удаленных сеансов открыть, одному для Скайп для бизнеса в Интернет, для Exchange Online и для системы безопасности &amp; центре соответствия требованиям (его можно может иметь больше, чем три удаленного сеансы запущена, в зависимости от того, является ли использовалась этот экземпляр Windows PowerShell для подключения к что-то еще, кроме служб Office 365). Вы должны увидеть, что-то следующим образом.
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

Чтобы закрыть эти три сеансы, выполните следующие команды по очереди. Первая команда закрывает Скайп для бизнеса в Интернет сеанса, второй закроется Exchange Online сеанса и третий закрывает безопасности &amp; сеанс центре соответствия требованиям.
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

При выполнении командлета **Get-PSSession** , не отобразится никаких вообще (если у вас есть другие удаленные сеансы запущены).
  
![Консоль Windows PowerShell без удаленных сеансов](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> Если вы хотите закрыть все удаленные сеансы в то же время, можно использовать следующую команду: >`Get-PSSession | Remove-PSSession`
  
Если вы сейчас попытаетесь выполнить командлет из любого из этих закрыт сеансов (например, **Get-CsMeetingConfiguration** в Скайп для бизнеса в Интернет) вы получите сообщение об ошибке, аналогичную этой.
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

Мы получаем этого сообщения об ошибке, так как командлеты для Скайп для бизнеса в Интернет, Exchange Online и безопасность &amp; центре соответствия требованиям были удалены при закрытии удаленных сеансов.
  
Чтобы закрыть сеанс SharePoint Online, введите следующую команду.
  
```
Disconnect-SPOService
```

Если вы сейчас попытаетесь выполнить командлет **Get-SPOSite** , вы получите сообщение об ошибке следующим образом.
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

Не удается получить сведения о сайте, поскольку вы больше не подключены к SharePoint Online.
  
Как для подключения к Office 365 хотя для командлета **Connect-MsolService** , нет нет соответствующих командлет **Disconnect-MsolService** . Поэтому для Office 365, просто закройте окно Windows PowerShell. Тем не менее, это по-прежнему рекомендуется сделать это последний, поэтому можно надлежащим образом отключить из SharePoint Online, Скайп для бизнеса в Интернет, Exchange Online и безопасность &amp; центре соответствия требованиям.
  
## <a name="new-to-office-365"></a>Никогда не работали с Office 365?
<a name="LongVersion"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>См. также

#### 

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Управление SharePoint Online с помощью Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
  
[Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Использование Windows PowerShell для создания отчетов в Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

