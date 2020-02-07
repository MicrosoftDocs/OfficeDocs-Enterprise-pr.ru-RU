---
title: Подключение к Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Сводка. Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.
ms.openlocfilehash: 96ad47e6f60d6e098deffb48c56b4004d732b033
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844260"
---
# <a name="connect-to-office-365-powershell"></a>Подключение к Office 365 PowerShell

PowerShell в Office 365 позволяет управлять параметрами Office 365 из командной строки. Подключение к PowerShell в Office 365 — это простой процесс установки необходимого программного обеспечения и последующего подключения к организации Office 365. 

Существует две версии модуля PowerShell, которые используются для подключения к Office 365 и управления учетными записями пользователей, группами и лицензиями:

- Azure Active Directory PowerShell для Graph (командлеты содержат **AzureAD** в своем имени)
- Модуль Microsoft Azure Active Directory для Windows PowerShell (командлеты содержат **MSol** в своем имени) 

На момент выхода этой статьи модуль Azure Active Directory PowerShell для Graph не полностью заменяет функции командлетов модуля Microsoft Azure Active Directory для Windows PowerShell при администрировании пользователей, групп и лицензий. Во многих случаях необходимо использовать обе версии. Вы можете безопасно установить обе версии на одном компьютере.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы?

Ниже приведены версии Windows, которые можно использовать.
    
  - Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2 SP1

    > [!NOTE]
    > Требуется использовать PowerShell версии 5.1 или более поздней. Для Windows 8.1, Windows 8, Windows 7 с пакетом обновления 1 (SP1), Windows Server 2012 R2, Windows Server 2012 и Windows Server 2008 R2 SP1 скачайте и установите [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616). 
    
    > [!NOTE]
    >Используйте 64-разрядную версию Windows. Поддержка 32-разрядной версии модуля Microsoft Azure Active Directory для Windows PowerShell прекращена в октябре 2014 г.
    
Эти процедуры предназначены для пользователей, являющихся участниками роли администратора Office 365. Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Подключение к модулю Azure Active Directory PowerShell для Graph

Имена командлетов в модуле [Azure Active Directory PowerShell для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) включают компонент **AzureAD**.

Чтобы выполнить действия, требующие использования новых командлетов в модуле Azure Active Directory PowerShell для Graph, установите его и подключитесь к подписке на Office 365. Вот как это сделать:

>[!Note]
>Информацию о поддержке в различных версиях Microsoft Windows см. в [этой статье](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
>

### <a name="step-1-install-required-software"></a>Шаг 1. Установите необходимое программное обеспечение

Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.
  
1. Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).
    
2. В командном окне **Администратор: Windows PowerShell** выполните следующую команду:
    
  ```powershell
  Install-Module -Name AzureAD
  ```

Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Шаг 2. Подключитесь к Azure AD для своей подписки Office 365

Чтобы подключиться к Azure AD для своей подписки на Office 365 с помощью имени учетной записи и пароля или с помощью многофакторной проверкой подлинности (MFA), запустите одну из этих команд в командной строке Windows PowerShell (повышенные привилегии не требуются).

|||
|:-------|:-----|
| **Облачная служба Office 365** | **Команда** |
| Office 365 Worldwide (+GCC) | `Connect-AzureAD` |
| Office 365, предоставляемый 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 для DoD государственных организаций США и Office 365 для GCC High государственных организаций США | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

В диалоговом окне **Вход в учетную запись** введите имя пользователя и пароль своей рабочей или учебной учетной записи Office 365 и нажмите кнопку **ОК**.

Если вы используете многофакторную проверку подлинности, следуйте инструкциям в дополнительных диалоговых окнах, чтобы предоставить дополнительные сведения для проверки подлинности, например код проверки.

После подключения можно использовать командлеты для [модуля Azure Active Directory PowerShell для Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Подключение к модулю Microsoft Azure Active Directory для Windows PowerShell

Имена командлетов в модуле Microsoft Azure Active Directory для Windows PowerShell включают компонент **Msol**.

>[!Note]
>В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени. Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>
    
### <a name="step-1-install-required-software"></a>Шаг 1. Установите необходимое программное обеспечение

Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.
  
1.  Установите 64-разрядную версию помощника по входу в Microsoft Online Services. См. статью [Помощник по входу в Microsoft Online Services для ИТ-специалистов, RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Чтобы установить модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:
    
  - Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).
  - Выполните команду **Install-Module MSOnline**.
  - Если отобразится запрос на установку поставщика NuGet, введите **Y** и нажмите клавишу ВВОД.
  - Если отобразится запрос на установку модуля из репозитория PSGallery, введите **Y** и нажмите клавишу ВВОД.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Шаг 2. Подключитесь к Azure AD для своей подписки Office 365

Чтобы подключиться к Azure AD для своей подписки на Office 365 с помощью имени учетной записи и пароля или с помощью многофакторной проверкой подлинности (MFA), запустите одну из этих команд в командной строке Windows PowerShell (повышенные привилегии не требуются).

|||
|:-------|:-----|
| **Облачная служба Office 365** | **Команда** |
| Office 365 Worldwide (+GCC) | `Connect-MsolService` |
| Office 365, предоставляемый 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 для DoD государственных организаций США и Office 365 для GCC High государственных организаций США | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

В диалоговом окне **Вход в учетную запись** введите имя пользователя и пароль своей рабочей или учебной учетной записи Office 365 и нажмите кнопку **ОК**.

Если вы используете многофакторную проверку подлинности, следуйте инструкциям в дополнительных диалоговых окнах, чтобы предоставить дополнительные сведения для проверки подлинности, например код проверки.

### <a name="how-do-you-know-this-worked"></a>Как проверить, все ли получилось?

Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.
  
Если возникают ошибки, просмотрите список возможных причин ниже.
  
- **Распространенная проблема  неправильный пароль.**. Еще раз выполните шаг 2, внимательно проверив вводимое имя пользователя и пароль.
    
- **Для работы модуля Microsoft Azure Active Directory для Windows PowerShell необходимо, чтобы на вашем компьютере был включен компонент Microsoft .NET Framework 3.5.* x*. Скорее всего, на вашем компьютере установлена более новая версия этого компонента (например, 4 или 4.5.* x*), но вы можете включить или отключить режим обратной совместимости с более ранними версиями платформы .NET Framework. Дополнительную информацию см. в следующих статьях:
    
  - [Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)
    
  - [Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)

  - [Установка платформы .NET Framework 3.5 на Windows 10, Windows 8.1 и Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10) (Windows 10, Windows 8.1 и Windows 8)

  
- **Возможно, используемая вами версия Модуль Microsoft Azure Active Directory для Windows PowerShell устарела.** Чтобы проверить актуальность версии, выполните указанную ниже команду в PowerShell в Office 365 или в Модуль Microsoft Azure Active Directory для Windows PowerShell.
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Если возвращенный номер версии будет меньше 1.0.8070.2, удалите Модуль Microsoft Azure Active Directory для Windows PowerShell и установите последнюю версию, скачав ее по ссылке, указанной на шаге 1.
    
- **Если при подключении возникнет ошибка, ознакомьтесь с **[этой статьей](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    

## <a name="see-also"></a>См. также

- [Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
- [Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
