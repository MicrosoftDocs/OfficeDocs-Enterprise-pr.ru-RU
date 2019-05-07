---
title: Подключение к Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Сводка. подключение к организации Office 365 с помощью PowerShell в Office 365 для выполнения задач центра администрирования из командной строки.
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639780"
---
# <a name="connect-to-office-365-powershell"></a>Подключение к Office 365 PowerShell

 **Сводка:** Подключитесь к вашей организации Office 365 с помощью Office 365 PowerShell, чтобы выполнять задачи администрирования из командной строки.
  
Office 365 PowerShell позволяет управлять параметрами Office 365 из командной строки. Подключение к Office 365 PowerShell — это простой процесс установки необходимого программного обеспечения и последующего подключения к организации Office 365. 

Существует две версии модуля PowerShell, которые используются для подключения к Office 365 и управления учетными записями пользователей, группами и лицензиями.

- Azure Active Directory PowerShell для Graph (командлеты содержат **AzureAD** в своем имени) 
- Модуль Microsoft Azure Active Directory для Windows PowerShell (командлеты содержат **MSol** в своем имени) 

Начиная с даты этой статьи, модуль Azure Active Directory PowerShell для Graph не полностью заменяет функции командлетов модуля Microsoft Azure Active Directory для модуля Windows PowerShell для администрирования пользователей, групп и лицензий. . Во многих случаях необходимо использовать обе версии. Вы можете безопасно установить обе версии на одном компьютере.

> [!TIP]
> **Никогда не работали с PowerShell?** Посмотрите [этот видеообзор](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) на сайте LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы?

- Предполагаемое время для завершения: 5 минут.
    
- Ниже приведены версии Windows, которые можно использовать.
    
  - Windows 10, Windows 8,1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2 с ПАКЕТом обновления 1 (SP1)
    
    > [!NOTE]
    >Используйте 64-разрядную версию Windows. Поддержка 32-разрядной версии модуля Microsoft Azure Active Directory для Windows PowerShell прекращена в октябре 2014 г.
    
-  Эти процедуры предназначены для пользователей, которые являются участниками роли администратора Office 365. Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Подключение к модулю PowerShell Azure Active Directory PowerShell для Graph

Команды в модуле [PowerShell Azure Active Directory для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) содержат **AzureAD** в имени командлета.

Для выполнения процедур, требующих новых командлетов в модуле PowerShell Azure Active Directory PowerShell для Graph, выполните указанные ниже действия, чтобы установить модуль и подключиться к вашей подписке на Office 365.

>[!Note]
>Сведения о поддержке различных версий Microsoft Windows можно найти в [модуле PowerShell Azure Active Directory PowerShell для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .
>

### <a name="step-1-install-required-software"></a>Шаг 1. Установите необходимое программное обеспечение

Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.
  
1. Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).
    
2. В командном окне **Администратор: Windows PowerShell** выполните следующую команду:
    
  ```
  Install-Module -Name AzureAD
  ```

Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Шаг 2: подключение к Azure AD для подписки на Office 365

Чтобы подключиться к Azure AD для вашей подписки на Office 365 с помощью имени учетной записи и пароля или с многофакторной проверкой подлинности *(MFA)*, запустите одну из этих команд из командной строки Windows PowerShell (нет прав на повышение).

|||
|:-------|:-----|
| **Office 365, облако** | **Command** |
| Office 365 для разных языков (+ GCC) | `Connect-AzureAD` |
| Office 365 под управлением 21 ВИАНЕТ | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 в Германии | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 для государственных учреждений (США) и Office 365 для государственных учреждений (США) GCC (высокое) | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

В диалоговом окне **Вход в учетную запись** введите имя пользователя и пароль учетной записи Office 365 Work или School, а затем нажмите кнопку **ОК**.

Если используется MFA, следуйте инструкциям в дополнительных диалоговых окнах, чтобы получить дополнительные сведения о проверке подлинности, например код проверки.


После подключения вы можете использовать новые командлеты для [модуля Azure Active Directory PowerShell для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Подключение к модулю Microsoft Azure Active Directory для Windows PowerShell

Имена командлетов в модуле Microsoft Azure Active Directory для Windows PowerShell включают компонент **Msol**.
    
### <a name="step-1-install-required-software"></a>Шаг 1. Установите необходимое программное обеспечение

Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.
  
1.  Установите 64-разрядную версию помощника по входу в Microsoft Online Services. См. статью [Помощник по входу в Microsoft Online Services для ИТ-специалистов, RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Чтобы установить модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:
    
  - Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).
  - Выполните команду **Install-Module MSOnline**.
  - Если отобразится запрос на установку поставщика NuGet, введите **Y** и нажмите клавишу ВВОД.
  - Если отобразится запрос на установку модуля из репозитория PSGallery, введите **Y** и нажмите клавишу ВВОД.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Шаг 2: подключение к Azure AD для подписки на Office 365

Чтобы подключиться к Azure AD для вашей подписки на Office 365 с помощью имени учетной записи и пароля или с многофакторной проверкой подлинности *(MFA)*, запустите одну из этих команд из командной строки Windows PowerShell (нет прав на повышение).

|||
|:-------|:-----|
| **Office 365, облако** | **Command** |
| Office 365 для разных языков (+ GCC) | `Connect-MsolService` |
| Office 365 под управлением 21 ВИАНЕТ | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 в Германии | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 для государственных учреждений (США) и Office 365 для государственных учреждений (США) GCC (высокое) | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

В диалоговом окне **Вход в учетную запись** введите имя пользователя и пароль учетной записи Office 365 Work или School, а затем нажмите кнопку **ОК**.

Если используется MFA, следуйте инструкциям в дополнительных диалоговых окнах, чтобы получить дополнительные сведения о проверке подлинности, например код проверки.

### <a name="how-do-you-know-this-worked"></a>Как убедиться, что все получилось?

Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.
  
Если возникают ошибки, просмотрите список возможных причин:
  
- **Распространенная проблема  неправильный пароль.**. Еще раз выполните шаг 2. Будьте особенно внимательны при вводе имени пользователя и пароля.
    
- * *Для работы модуля Microsoft Azure Active Directory для Windows PowerShell требуется платформа Microsoft .net Framework 3,5.* функция x * включена на вашем компьютере * *. Вероятно, на компьютере установлена более новая версия (например, 4 или 4,5).* x *), но обратная совместимость с более ранними версиями .NET Framework может быть включена или отключена. Дополнительную информацию см. в следующих статьях:
    
  - [Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)
    
  - [Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)

  - Для Windows 10, Windows 8,1 и Windows 8 Ознакомьтесь со статьей [Установка платформы .NET Framework 3,5 в Windows 10, windows 8,1 и Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
- **Возможно, используемая вами версия Модуль Microsoft Azure Active Directory для Windows PowerShell устарела.** Чтобы проверить актуальность версии, выполните указанную ниже команду в PowerShell в Office 365 или в Модуль Microsoft Azure Active Directory для Windows PowerShell.
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Если возвращенный номер версии будет меньше 1.0.8070.2, удалите Модуль Microsoft Azure Active Directory для Windows PowerShell и установите последнюю версию, скачав ее по ссылке, указанной на шаге 1.
    
- **Если при подключении возникнет ошибка, ознакомьтесь с **[этой статьей](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    

## <a name="see-also"></a>См. также

- [Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
- [Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

