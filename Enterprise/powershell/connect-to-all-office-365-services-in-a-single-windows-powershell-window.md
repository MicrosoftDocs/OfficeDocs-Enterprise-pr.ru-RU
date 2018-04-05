---
title: Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
description: 'Сводка: Подключение Windows PowerShell для всех служб Office 365 в одном окне Windows PowerShell.'
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell

 **Сводка:** Вместо управление различных службах Office 365 в отдельной консоли windows PowerShell можно подключиться ко всем службам Office 365 и управлять ими из одного окна консоли.
  
При использовании PowerShell для управления Office 365, его можно установить до пяти различных Windows PowerShell открытые в то же время, соответствующий центра администрирования Office 365, SharePoint Online, Exchange Online, Скайп для бизнеса в Интернет и безопасности &amp;Центре соответствия требованиям. С помощью пяти разные способы подключения в отдельных сеансах Windows PowerShell к рабочему столу может выглядеть следующим образом:
  
![Пять консолей Windows PowerShell, работающих одновременно](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Это не является оптимальным для управления Office 365, так как не удается обмен данными между этих пяти windows для управления между службами. В этом разделе описывается, как использовать один экземпляр Windows PowerShell, из которого можно управлять Office 365, Скайп для бизнеса в Интернет, Exchange Online, SharePoint Online и безопасность &amp; центре соответствия требованиям.

>[!Note]
>В этой статье — в процессе обновления для использования модуля Azure Active Directory версии 2 PowerShell, а также для многофакторная проверка подлинности (многофакторной проверкой Подлинности).
>
  
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
    
    * Необходимо установить Microsoft .NET Framework 4.5. *x* и затем либо Windows Management Framework 3.0 или Windows Management Framework 4.0. Для получения дополнительных сведений см [установки .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) и [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) или [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Необходимо использовать 64-разрядной версии Windows из-за требования к Скайп для бизнеса в Интернет в модуле и один из модулей Office 365.
    
- Требуется ли установить модули, которые необходимы для Office 365, SharePoint Online и Скайп для бизнеса в Интернет:
    
   - [Microsoft Online службы помощник по входу для ИТ-специалистов RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - Windows Azure Active Directory модуль для Windows PowerShell (64-разрядная версия) с помощью команды **Install-модуль MSOnline** в командной строке с повышенными привилегиями PowerShell.
   - [Командная консоль SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Скайп для бизнеса через Интернет, модуля Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell необходимо настроить для запуска сценариев со знаком для Скайп для бизнеса в Интернет, Exchange Online и безопасность &amp; центре соответствия требованиям. Для этого выполните следующую команду в сеансе Windows PowerShell с повышенными привилегиями (окно Windows PowerShell можно открыть, выбрав **Запуск от имени администратора**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a>Действия подключения
<a name="BeforeYouBegin"> </a>

Далее приведены шаги для подключения к службам в одном окне PowerShell.
  
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

## <a name="new-to-office-365"></a>Никогда не работали с Office 365?
<a name="LongVersion"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>См. также

- [Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
- [Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Управление SharePoint Online с помощью Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Использование Windows PowerShell для создания отчетов в Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
