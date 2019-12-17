---
title: Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
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
description: 'Сводка: подключение Windows PowerShell ко всем службам Office 365 в отдельном окне Windows PowerShell.'
ms.openlocfilehash: ec24914367450e4ff464b3399be9cb2e626dd254
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072511"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell

При использовании PowerShell для управления Office 365 можно одновременно открыть до пяти разных сеансов Windows PowerShell, соответствующих центру администрирования Microsoft 365, SharePoint Online, Exchange Online, Skype для бизнеса Online и центром безопасности &amp; и соответствия требованиям. С пятью методами подключения, которые находятся в разных сеансах Windows PowerShell, ваш рабочий стол может выглядеть следующим образом:
  
![Пять консолей Windows PowerShell, работающих одновременно](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Это не является оптимальным для управления Office 365, так как вы не можете обмениваться данными между этими пятью окнами для управления в нескольких службах. В этом разделе описывается, как использовать один экземпляр Windows PowerShell, на котором можно управлять Office 365, Skype для бизнеса Online, Exchange Online, SharePoint Online и центром обеспечения безопасности &amp; .

>[!Note]
>В настоящее время эта статья содержит только команды для подключения к облаку Office 365 Worldwide (+ GCC). Дополнительные примечания содержат ссылки на статьи со сведениями о подключении к другим облакам Office 365.
>

## <a name="before-you-begin"></a>Перед началом работы

Прежде чем управлять всеми Office 365 из одного экземпляра Windows PowerShell, примите во внимание следующие предварительные требования:
  
- Рабочая или учебная учетная запись Office 365, используемая для выполнения этих процедур, должна быть членом роли администратора Office 365. Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Это требование для Office 365 PowerShell, не обязательно для всех остальных служб Office 365.
    
- Ниже приведены 64-разрядные версии Windows, которые можно использовать.
    
  - Windows 10
    
  - Windows 8.1 или Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 или Windows Server 2012
    
  - Windows 7 с пакетом обновления 1 (SP1)*
    
  - Windows Server 2008 R2 с пакетом обновления 1 (SP1)*
    
    \*Необходимо установить Microsoft .NET Framework 4,5. *x* , а затем — Windows management Framework 3,0 или Windows management Framework 4,0. Дополнительные сведения см. [в статье Установка .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) и [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Необходимо использовать 64-разрядную версию Windows из-за требований для модуля Skype для бизнеса Online и одного из модулей Office 365.
    
- Необходимо установить модули, необходимые для Azure AD, SharePoint Online и Skype для бизнеса Online:
    
   - [Azure Active Directory v2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [Командная консоль SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype для бизнеса Online, модуль Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Необходимо настроить Windows PowerShell, чтобы выполнять подписанные сценарии для Skype для бизнеса Online, Exchange Online и центра безопасности &amp; и соответствия требованиям. Для этого выполните следующую команду в сеансе Windows PowerShell с повышенными привилегиями (для этого выберите пункт **Запуск от имени администратора**).
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Шаги подключения при использовании пароля

Ниже описаны действия, которые необходимо выполнить для подключения ко всем службам в отдельном окне PowerShell.
  
1. Откройте Windows PowerShell от имени администратора (используйте **Запуск от имени администратора**).
    
2. Выполните эту команду и введите учетные данные рабочей или учебной учетной записи Office 365.
    
  ```powershell
  $credential = Get-Credential
  ```

3. Выполните эту команду для подключения к Azure Active Directory (AD) с помощью модуля PowerShell Azure Active Directory PowerShell для Graph.
    
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

4. Выполните указанные ниже команды, чтобы подключиться к SharePoint Online. Замените _ \<домаинхост>_ на фактическое значение для вашего домена. Например, для "litwareinc.onmicrosoft.com" _ \<домаинхост>_ значение "litwareinc".
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Выполните приведенные ниже команды, чтобы подключиться к Skype для бизнеса Online. Предупреждение об увеличении `WSMan NetworkDelayms` значения ожидается при первом подключении и должно быть проигнорировано.
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Выполните эти команды для подключения к Exchange Online.
    
  ```powershell
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
>Чтобы подключиться к Exchange Online для офисов Office 365, отличных от мира, ознакомьтесь со статьей [Подключение к Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
>

7. Выполните приведенные ниже команды, чтобы подключиться &amp; к центру соответствия требованиям безопасности.
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>Чтобы подключиться к центру соответствия &amp; требованиям безопасности для облаков Office 365, отличных от мира, ознакомьтесь со статьей [подключение к office 365 Security & центра соответствия требованиям PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
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
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
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
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Когда вы будете готовы закрыть окно Windows PowerShell, выполните следующую команду, чтобы удалить активные сеансы связи с Skype для бизнеса Online, Exchange Online, SharePoint Online и центром безопасности &amp; и соответствия требованиям.
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Шаги подключения при использовании многофакторной проверки подлинности

Ниже приведены все команды в едином блоке для подключения к Azure AD, SharePoint Online и Skype для Буинесс с использованием многофакторной проверки подлинности в отдельном окне с помощью модуля Azure Active Directory PowerShell для Graph. Укажите имя участника-пользователя (UPN) для учетной записи пользователя и имя узла домена, а затем запустите их в один раз.

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
```

Для Exchange Online и центра соответствия &amp; требованиям безопасности ознакомьтесь со следующими разделами, чтобы подключиться с использованием многофакторной проверки подлинности:

- [Подключение к Exchange Online PowerShell с помощью многофакторной проверки подлинности](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Подключение к PowerShell центра безопасности & центра соответствия требованиям Office 365 с использованием многофакторной проверки подлинности](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
Обратите внимание, что в обоих случаях необходимо подключаться с помощью отдельных сеансов удаленного модуля PowerShell Exchange Online.


## <a name="see-also"></a>См. также

- [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md)
- [Управление SharePoint Online с помощью Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Использование Windows PowerShell для создания отчетов в Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
