---
title: Подключение ко всем службам Microsoft 365 в отдельном окне Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Сводка: подключение Windows PowerShell ко всем службам Microsoft 365 в отдельном окне Windows PowerShell.'
ms.openlocfilehash: a037de53dcbf8fed95b9b4d5f05677997135dfb3
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230845"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a>Подключение ко всем службам Microsoft 365 в отдельном окне Windows PowerShell

При использовании PowerShell для управления Microsoft 365 можно одновременно открыть до пяти разных сеансов Windows PowerShell, соответствующих центру администрирования Microsoft 365, SharePoint Online, Exchange Online, Skype для бизнеса Online, Microsoft Teams и центре безопасности и &amp; соответствия требованиям. С пятью методами подключения, которые находятся в разных сеансах Windows PowerShell, ваш рабочий стол может выглядеть следующим образом:
  
![Пять консолей Windows PowerShell, работающих одновременно](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Это не является оптимальным решением для управления Microsoft 365, так как вы не можете обмениваться данными между этими пятью окнами для управления в нескольких службах. В этом разделе описывается, как использовать один экземпляр Windows PowerShell, на котором можно управлять учетными записями Microsoft 365, Skype для бизнеса Online, Exchange Online, SharePoint Online, Microsoft Teams и &amp; центром безопасности.

>[!Note]
>В настоящее время эта статья содержит только команды для подключения к облаку в мире (+ GCC). Дополнительные примечания содержат ссылки на статьи со сведениями о подключении к другим облакам Microsoft 365.
>

## <a name="before-you-begin"></a>Прежде чем начать

Прежде чем управлять всеми Microsoft 365 с помощью одного экземпляра Windows PowerShell, примите во внимание следующие требования:
  
- Рабочая или учебная учетная запись Microsoft 365, используемая для выполнения этих процедур, должна быть членом роли администратора Microsoft 365. Дополнительные сведения см. в статье [О ролях администраторов](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide). Это требование для PowerShell для Microsoft 365, не обязательно для всех остальных служб Microsoft 365.
    
- Ниже приведены 64-разрядные версии Windows, которые можно использовать.
    
  - Windows 10
    
  - Windows 8.1 или Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 или Windows Server 2012
    
  - Windows 7 с пакетом обновления 1 (SP1)*
    
  - Windows Server 2008 R2 с пакетом обновления 1 (SP1)*
    
    \*Необходимо установить Microsoft .NET Framework 4,5. *x* , а затем — Windows management Framework 3,0 или Windows management Framework 4,0. Дополнительные сведения см. [в статье Установка .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) и [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Необходимо использовать 64-разрядную версию Windows из-за требований для модуля Skype для бизнеса Online и одного из модулей Microsoft 365.
    
- Необходимо установить модули, необходимые для Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype для бизнеса Online и teams:
    
   - [Azure Active Directory v2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [Командная консоль SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype для бизнеса Online, модуль Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Exchange Online PowerShell v2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [Общие сведения о Teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  Необходимо настроить Windows PowerShell, чтобы выполнять подписанные сценарии для Skype для бизнеса Online и &amp; центра соответствия требованиям безопасности. Для этого выполните следующую команду в сеансе Windows PowerShell с повышенными привилегиями (для этого выберите пункт **Запуск от имени администратора**).
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-just-a-password"></a>Шаги подключения при использовании только пароля

Ниже приведены действия по подключению ко всем службам в отдельном окне PowerShell, когда вы используете только пароль для входа в систему.
  
1. Откройте командную консоль Windows PowerShell.
    
2. Выполните указанную ниже команду и введите учетные данные учетной записи Microsoft 365 Рабочая или учебной учетной записи.
    
  ```powershell
  $credential = Get-Credential
  ```

3. Выполните эту команду, чтобы подключиться к Azure AD с помощью модуля PowerShell Azure Active Directory PowerShell для Graph.
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  Кроме того, если вы используете модуль Microsoft Azure Active Directory Module для Windows PowerShell, выполните указанную ниже команду.
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
>В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени. Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>

4. Выполните указанные ниже команды, чтобы подключиться к SharePoint Online. Укажите название организации для вашего домена. Например, для "litwareinc.onmicrosoft.com" в качестве имени организации используется значение "litwareinc".
    
  ```powershell
  $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
  Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
  ```

5. Выполните приведенные ниже команды, чтобы подключиться к Skype для бизнеса Online. Предупреждение об увеличении `WSMan NetworkDelayms` значения ожидается при первом подключении и должно быть проигнорировано.
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Выполните эту команду, чтобы подключиться к Exchange Online.
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
>Чтобы подключиться к Exchange Online для других облаков Microsoft 365, используйте параметр **-ексчанжеенвиронментнаме** . Для получения дополнительных сведений обратитесь [к раздел Connect – ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) .
>

7. Выполните эти команды для подключения к PowerShell Teams PowerShell.
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
>Чтобы подключиться к облакам Microsoft Teams, не по всему миру, ознакомьтесь с разделом [Connect – MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).
>

8. Выполните приведенные ниже команды, чтобы подключиться к &amp; центру соответствия требованиям безопасности.
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>Чтобы подключиться к &amp; центру соответствия требованиям безопасности для других облаков Microsoft 365, которые не находятся в разных странах мира, обратитесь к разделу [Connect to Security & The PowerShell Center](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
>

Ниже приведены все команды в отдельном блоке при использовании модуля Azure Active Directory PowerShell для Graph. Укажите имя узла домена, а затем выполните все сразу.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Кроме того, здесь приведены все команды в едином блоке при использовании модуля Microsoft Azure Active Directory для модуля Windows PowerShell. Укажите имя узла домена, а затем выполните все сразу.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Когда вы будете готовы закрыть окно Windows PowerShell, выполните следующую команду, чтобы удалить активные сеансы в Skype для бизнеса Online, SharePoint Online, &amp; центре безопасности и соответствия требованиям teams:
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Шаги подключения при использовании многофакторной проверки подлинности

Ниже приведены все команды в едином блоке для подключения к Azure AD, SharePoint Online, Skype для бизнеса, Exchange Online и Teams с использованием многофакторной проверки подлинности в отдельном окне с помощью модуля Azure Active Directory PowerShell для Graph. Укажите имя участника-пользователя (UPN) для учетной записи пользователя и имя узла домена, а затем запустите их в один раз.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

Кроме того, при использовании модуля Microsoft Azure Active Directory для Windows PowerShell можно использовать и все команды.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

В центре безопасности и соответствия требованиям Узнайте, как подключить многофакторную проверку подлинности для &amp; подключения с использованием многофакторной проверки подлинности в [PowerShell центра безопасности & соответствия требованиям](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) .

## <a name="see-also"></a>См. также

- [Подключение к Microsoft 365 с помощью PowerShell](connect-to-office-365-powershell.md)
- [Управление SharePoint Online с помощью PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Управление учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Использование Windows PowerShell для создания отчетов в Microsoft 365](use-windows-powershell-to-create-reports-in-office-365.md)
