---
title: "Подключение к Office 365 PowerShell"
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
- O365ITProTrain
- DecEntMigration
- apr17entnews
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Сводка: Подключиться к своей организации Office 365, с помощью Office 365 PowerShell для выполнения задачи в центр администрирования Office 365 с помощью командной строки."
ms.openlocfilehash: 3ac368a3d3584c15e1d0c26104616e8258a78e7b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-office-365-powershell"></a>Подключение к Office 365 PowerShell

 **Сводка:** Подключение к организации Office 365 с помощью Office 365 PowerShell для выполнения задач администрирования Office 365 с помощью командной строки.
  
Office 365 PowerShell позволяет Управление параметрами Office 365 с помощью командной строки. Подключение к Office 365 PowerShell — простой процесс трех этапов, где Установка необходимого программного обеспечения, запустите необходимого программного обеспечения и затем подключиться к своей организации Office 365. 

Обратите внимание, что эти инструкции подключения такие же, как в разделе [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).
  
> [!TIP]
> **Новые PowerShell?** Просмотрите [Видео Обзор PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), с LinkedIn обучения. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы

- Предполагаемое время для завершения: 5 минут.
    
- Ниже приведены версии Windows, которые можно использовать.
    
  - Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2 с пакетом обновления 1
    
    > [!NOTE]
    >Использование 64-разрядной версии Windows. Поддержка 32-разрядная версия Microsoft Azure модуль Active Directory для Windows PowerShell была удаленные в октября 2014 г.
    
-  Office 365 работы или школе учетной записи, используемой для этих процедур потребностей для быть участником роли администратора Office 365. Дополнительные сведения см в [роли администраторов об Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).
    
## <a name="step-1-install-required-software"></a>Шаг 1. Установите необходимое программное обеспечение

Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.
  
1.  Установка 64-разрядной версии Microsoft Online Services помощник по входу: [Microsoft Online Services помощник по входу для RTW специалистов ИТ](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Чтобы установить 64-разрядную версию Модуль Microsoft Azure Active Directory для Windows PowerShell, сделайте следующее:
    
  - Откройте веб-страницу [Подключение к Azure Active Directory](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185).
    
  - В разделе **Files in Download** (Файлы в пакете) в нижней части страницы нажмите **Download** (Скачать) напротив файла **AdministrationConfig-V1.1.166.0-GA.msi**, а затем установите его.
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a>Шаг 2. Откройте модуль Windows Azure Active Directory

1. Найдите и откройте Модуль Microsoft Azure Active Directory для Windows PowerShell с помощью одного из указанных ниже методов (в зависимости от используемой версии Windows).
    
  - **Меню "Пуск".** На рабочем столе нажмите **Пуск** и введитеAzure.
    
  - **Без использования меню "Пуск":** выполните поискAzure любым из указанных ниже методов.
    
  - На начальном экране щелкните пустую область и введите Azure.
    
  - На рабочем столе или на начальном экране нажмите клавиши Windows+Q. В чудо-кнопке "Поиск" введите Azure.
    
  - На рабочем столе или на начальном экране переместите курсор в правом верхнем углу или проведите слева от правого края экрана, чтобы отобразить чудо-кнопки. Выберите чудо поиска и введите **Azure**.
    
2. В списке результатов выберите **Модуль Microsoft Azure Active Directory для Windows PowerShell**.
    
## <a name="step-3-connect-to-your-office-365-subscription"></a>Шаг 3. Подключитесь к своей подписке Office 365:
<a name="step3"> </a>

Чтобы использовать только  *имя и пароль учетной записи*  :
  
1. В командном окне **Модуль Microsoft Azure Active Directory для Windows PowerShell** выполните следующие команды.
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свои имя пользователя и пароль Office 365:рабочая или учебная учетная запись, а затем нажмите кнопку **ОК**.
    
Чтобы использовать  *многофакторную проверку подлинности (MFA)*  :
  
1. В командном окне **Модуль Microsoft Azure Active Directory для Windows PowerShell** выполните следующую команду.
    
  ```
  Connect-MsolService
  ```

2. В диалоговом окне **Azure Active Directory PowerShell** введите имя пользователя и пароль рабочей или учебной учетной записи Office 365 и нажмите **Войти**.
    
3. Следуйте инструкциям в диалоговом окне **Azure Active Directory PowerShell**, чтобы указать дополнительные сведения для проверки подлинности, например код подтверждения, и нажмите **Войти**.
    
## <a name="how-do-you-know-this-worked"></a>Как проверить, что все получилось?
<a name="step3"> </a>

Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.
  
Если возникают ошибки, просмотрите список возможных причин:
  
- **Распространенная проблема  неправильный пароль.**. Еще раз выполните шаг 3. Будьте особенно внимательны при вводе имени пользователя и пароля.
    
- **Для работы Модуль Microsoft Azure Active Directory для Windows PowerShell необходимо, чтобы на вашем компьютере был включен компонент Платформа Microsoft .NET Framework 3.5. _x_**. Скорее всего, на вашем компьютере будет установлена более новая версия этого компонента (например, 4 или 4.5. _x_), но вы можете включить или отключить режим обратной совместимости с более ранними версиями Платформа .NET Framework. Дополнительные сведения см. в указанных ниже статьях.
    
  - Windows Server 2012 или Windows Server 2012 R2 в разделе [Включение .NET Framework 3.5 с помощью мастера функций и добавления ролей](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Windows 8 или Windows 8.1 в разделе [Установка .NET Framework 3.5 в Windows 8 или 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - Windows 7 или Windows Server 2008 R2 можно [не могут открыть Azure модуль Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **Возможно, используемая вами версия Модуль Microsoft Azure Active Directory для Windows PowerShell устарела.** Чтобы проверить актуальность версии, выполните указанную ниже команду в PowerShell в Office 365 или в Модуль Microsoft Azure Active Directory для Windows PowerShell.
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Если возвращенный номер версии будет меньше 1.0.8070.2, удалите Модуль Microsoft Azure Active Directory для Windows PowerShell и установите последнюю версию, скачав ее по ссылке, указанной на шаге 1.
    
- **В случае ошибки подключения, см. в этом разделе:** [«Connect-MsolService: исключение типа» ошибка](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>Подключение с помощью модуля Azure Active Directory PowerShell 2
<a name="ConnectV2"> </a>

Чтобы выполнить действия, требующие использования новых командлетов в [модуле Azure Active Directory PowerShell 2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), установите его и подключитесь к подписке на Office 365. Вот как это сделать:
  
1. Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).
    
2. В командном окне **Администратор: Windows PowerShell** выполните следующую команду:
    
  ```
  Install-Module -Name AzureAD 
  ```

Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.
    
3. Когда установка нового модуля завершится, используйте эти команды для подключения к подписке на Office 365:
    
  -  С помощью *имени учетной записи и пароля*  :
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 В диалоговом окне **Запрос учетных данных Windows PowerShell** введите свои имя пользователя и пароль Office 365:рабочая или учебная учетная запись и нажмите кнопку **ОК**.
    
  - При  *многофакторной проверке подлинности (MFA)*  :
    
  ```
  Connect-AzureAD
  ```

В диалоговом окне **Azure Active Directory PowerShell** введите имя пользователя и пароль рабочей или учебной учетной записи Office 365 и нажмите **Войти**.
    
Следуйте инструкциям в диалоговом окне **Azure Active Directory PowerShell**, чтобы указать дополнительные сведения для проверки подлинности, например код подтверждения, и нажмите **Войти**.
    
После подключения можно использовать новые командлеты для [модуля Azure Active Directory PowerShell 2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  
## <a name="see-also"></a>See also

#### 

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Подключение ко всем службам Office 365 с помощью единого окна Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

