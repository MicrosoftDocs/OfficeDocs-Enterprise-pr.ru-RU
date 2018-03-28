---
title: Подключение к Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Сводка. Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.
ms.openlocfilehash: 7a76b0968ea5c3f214bf4e6c5b8e2e6f995386d6
ms.sourcegitcommit: 5b194d3d1c1fffe9c33747dd0118298326970ce7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="connect-to-office-365-powershell"></a>Подключение к Office 365 PowerShell

 **Сводка.** Подключитесь к своей организации Office 365, используя PowerShell, чтобы выполнять задачи администрирования из командной строки.
  
PowerShell позволяет управлять настройками Office 365 из командной строки. Подключение состоит из трех этапов: установки необходимого программного обеспечения, его запуска и непосредственно подключения к организации Office 365. 

Обратите внимание, что эти инструкции такие же, как в разделе [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).
  
> [!TIP]
> **Никогда не работали с PowerShell?** Посмотрите [этот видеообзор](https://support.office.com/ru-RU/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) на сайте LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы?

- Предполагаемое время для завершения: 5 минут.
    
- Ниже приведены версии Windows, которые можно использовать.
    
  - Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Используйте 64-разрядную версию Windows. Поддержка 32-разрядной версии модуля Microsoft Azure Active Directory для Windows PowerShell прекращена в октябре 2014 г.
    
-  Рабочая или учебная учетная запись Office 365, которая используется для этих процедур, должна иметь права администратора. Дополнительные сведения см. в статье [Роли администраторов в Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Подключение к модулю Microsoft Azure Active Directory для Windows PowerShell

Имена командлетов в модуле Microsoft Azure Active Directory для Windows PowerShell включают компонент **Msol**.
    
### <a name="step-1-install-required-software"></a>Шаг 1. Установите необходимое программное обеспечение

Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.
  
1.  Установите 64-разрядную версию помощника по входу в Microsoft Online Services. См. статью [Помощник по входу в Microsoft Online Services для ИТ-специалистов, RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Чтобы установить модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:
    
  - Откройте командную строку для уровня администратора PowerShell.
  - Выполните команду **Install-Module MSOnline**.
  - Если отобразится запрос на установку поставщика NuGet, введите **Y** и нажмите клавишу ВВОД.
  - Если отобразится запрос на установку модуля из репозитория PSGallery, введите **Y** и нажмите клавишу ВВОД.
  - После установки закройте командное окно PowerShell.
    
### <a name="step-2-connect-to-your-office-365-subscription"></a>Шаг 2. Подключитесь к своей подписке Office 365
<a name="step3"> </a>

Чтобы при подключении использовать только *имя и пароль учетной записи*:
  
1. Запустите командную строку Windows PowerShell.
2. В командном окне **Windows PowerShell** выполните следующие команды:
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свои имя пользователя и пароль Office 365:рабочая или учебная учетная запись и нажмите кнопку **ОК**.
    
Чтобы использовать *многофакторную проверку подлинности (MFA)*:
  
1. Запустите командную строку Windows PowerShell.
2. В командном окне **Модуль Microsoft Azure Active Directory для Windows PowerShell** выполните вот какую команду.
    
```
Connect-MsolService
```

3. В диалоговом окне **Azure Active Directory PowerShell** введите имя пользователя и пароль рабочей или учебной учетной записи Office 365 и нажмите **Войти**.
    
4. Следуйте инструкциям в диалоговом окне **Azure Active Directory PowerShell**, чтобы указать дополнительные сведения для проверки подлинности, например код подтверждения, и нажмите **Войти**.
    
### <a name="how-do-you-know-this-worked"></a>Как проверить, что все получилось?
<a name="step3"> </a>

Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.
  
Если возникают ошибки, просмотрите список возможных причин:
  
- **Распространенная проблема — неправильный пароль.**. Еще раз выполните шаг 3. Будьте особенно внимательны при вводе имени пользователя и пароля.
    
- **Для работы Модуль Microsoft Azure Active Directory для Windows PowerShell необходимо, чтобы на вашем компьютере был включен компонент Платформа Microsoft .NET Framework 3.5. _x_**. Скорее всего, на вашем компьютере будет установлена более новая версия этого компонента (например, 4 или 4.5. _x_), но вы можете включить или отключить режим обратной совместимости с более ранними версиями Платформа .NET Framework. Дополнительные сведения см. в указанных ниже статьях.
    
  - [Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)
    
  - [Установка .NET Framework 3.5 в Windows 8 или Windows 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369) (Windows 8 или Windows 8.1)
    
  - [Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)
    
- **Возможно, используемая вами версия Модуль Microsoft Azure Active Directory для Windows PowerShell устарела.** Чтобы проверить актуальность версии, выполните указанную ниже команду в PowerShell в Office 365 или в Модуль Microsoft Azure Active Directory для Windows PowerShell.
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Если возвращенный номер версии будет меньше 1.0.8070.2, удалите Модуль Microsoft Azure Active Directory для Windows PowerShell и установите последнюю версию, скачав ее по ссылке, указанной на шаге 1.
    
- **Если при подключении возникнет ошибка, ознакомьтесь с **[этой статьей](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>Подключение с помощью модуля Azure Active Directory PowerShell 2
<a name="ConnectV2"> </a>

Имена командлетов в модуле Azure Active Directory для PowerShell версии 2 включают компонент AzureAD.

Чтобы выполнить действия, требующие использования новых командлетов в [модуле Azure Active Directory для PowerShell версии 2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), установите его и подключитесь к подписке на Office 365. Вот как это сделать:

### <a name="step-1-install-required-software"></a>Шаг 1. Установите необходимое программное обеспечение

Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.

  
1. Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).
    
2. В командном окне **Администратор: Windows PowerShell** выполните следующую команду:
    
  ```
  Install-Module -Name AzureAD 
  ```

Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.


### <a name="step-2-connect-to-office-365"></a>Шаг 2. Подключитесь к Office 365

Чтобы подключиться к подписке на Office 365 с помощью *имени и пароля учетной записи*:
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свои имя пользователя и пароль Office 365:рабочая или учебная учетная запись и нажмите кнопку **ОК**.
    
Чтобы подключиться к подписке на Office 365 с использованием *многофакторной проверки подлинности (MFA)*:

```
Connect-AzureAD
```

В диалоговом окне **Azure Active Directory PowerShell** введите имя пользователя и пароль рабочей или учебной учетной записи Office 365 и нажмите **Войти**.
    
Следуйте инструкциям в диалоговом окне **Azure Active Directory PowerShell**, чтобы указать дополнительные сведения для проверки подлинности, например код подтверждения, и нажмите **Войти**.
    
После подключения можно использовать новые командлеты для [модуля Azure Active Directory PowerShell 2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  
## <a name="see-also"></a>См. также

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)

[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

