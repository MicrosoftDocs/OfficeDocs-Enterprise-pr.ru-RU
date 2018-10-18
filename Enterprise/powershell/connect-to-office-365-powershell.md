---
title: Подключение к Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
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
description: 'Сводка: Подключиться к своей организации Office 365, с помощью Office 365 PowerShell для выполнения задач Центр администрирования из командной строки.'
ms.openlocfilehash: 2ea9c3eaa9a589bed6bf7ac575ffd241b7a72f01
ms.sourcegitcommit: 8cacedcba4627042d4bd17f1a94fddcfd87f77b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2018
ms.locfileid: "25601643"
---
# <a name="connect-to-office-365-powershell"></a>Подключение к Office 365 PowerShell

 **Сводка:** Подключение к организации Office 365 с помощью Office 365 PowerShell для выполнения задач администрирования из командной строки.
  
Office 365 PowerShell позволяет Управление параметрами Office 365 с помощью командной строки. Подключение к Office 365 PowerShell — простой процесс, где Установка необходимого программного обеспечения, а затем подключиться к своей организации Office 365. 

Существует две версии модуль PowerShell, используемая для подключения к Office 365 и выполнять администрирование учетных записей пользователей, групп и лицензий.

- Azure Active Directory PowerShell для диаграммы (включая командлеты **AzureAD** именах) 
- Microsoft Azure модуль Active Directory для Windows PowerShell (включая командлеты **MSol** именах) 

По состоянию на дату в этой статье Azure Active Directory PowerShell для модуля график не полностью заменяет функциональные возможности в командлетах модуля Microsoft Azure модуль Active Directory для Windows PowerShell для пользователей, группы и Администрирование лицензирования . Во многих случаях необходимо использовать обеих версий. Безопасно обеих версиях можно установить на том же компьютере.

> [!TIP]
> **Никогда не работали с PowerShell?** Посмотрите [этот видеообзор](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) на сайте LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы?

- Предполагаемое время выполнения: 5 минут.
    
- Ниже приведены версии Windows, которые можно использовать.
    
  - Windows 10, Windows 8.1, Windows 8 или Windows 7 с пакетом обновления 1 (SP1) 
    
  - Windows Server 2019 Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 и Windows Server 2008 R2 с пакетом обновления 1
    
    > [!NOTE]
    >Используйте 64-разрядную версию Windows. Поддержка 32-разрядной версии модуля Microsoft Azure Active Directory для Windows PowerShell прекращена в октябре 2014 г.
    
-  Эти процедуры, предназначены для пользователей, являющихся членами роли администратора Office 365. Дополнительные сведения см в [роли администраторов об Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Связь с Azure Active Directory PowerShell для модуля "график"

Команды в модуле [Windows Azure Active Directory PowerShell для диаграммы](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) имеют **AzureAD** в имени командлета.

Для процедур, которые требуют новых командлетов в Windows Azure Active Directory PowerShell для модуля "график" используйте следующие действия для установки модуля и подключиться к своей подписке Office 365.

>[!Note]
>[Windows Azure Active Directory PowerShell для модуля "график"](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) в разделе сведения о поддержке для разных версий Microsoft Windows.
>

### <a name="step-1-install-required-software"></a>Шаг 1. Установите необходимое программное обеспечение

Указанные ниже действия необходимо выполнить на вашем компьютере только один раз (а не при каждом подключении). Тем не менее вам, скорее всего, придется периодически устанавливать более новые версии программного обеспечения.
  
1. Откройте командную строку Windows PowerShell с повышенными привилегиями (запустите Windows PowerShell от имени администратора).
    
2. В командном окне **Администратор: Windows PowerShell** выполните следующую команду:
    
  ```
  Install-Module -Name AzureAD
  ```

Если появится предупреждение об установке модуля из ненадежного репозитория, введите **Y** и нажмите клавишу ВВОД.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Шаг 2: Подключение к Azure AD для подписки Office 365

Чтобы подключиться к Azure AD для подписки Office 365 с имя учетной записи и пароль или *многофакторная проверка подлинности (многофакторной проверкой Подлинности)*, выполните следующую команду в командной строке Windows PowerShell (она не обязательно с повышенными привилегиями).
    
```
Connect-AzureAD
```

В диалоговом окне **входа в учетную запись** введите работы Office 365 или школа имя учетной записи и пароль и нажмите кнопку **ОК**.

При использовании многофакторной проверкой Подлинности следуйте инструкциям в диалоговых окнах дополнительные, чтобы предоставить дополнительные сведения о проверке подлинности, такие как код подтверждения.

>[!Tip]
>Для подключения к Office 365 Германия видеть [подключение к Германии Azure с помощью PowerShell](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps).
>
    
После подключения, можно использовать новые командлеты для [Windows Azure Active Directory PowerShell для модуля "график"](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

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
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Шаг 2: Подключение к Azure AD для подписки Office 365

Чтобы подключиться к Azure AD для подписки Office 365 с имя учетной записи и пароль или *многофакторная проверка подлинности (многофакторной проверкой Подлинности)*, выполните следующую команду в командной строке Windows PowerShell (она не обязательно с повышенными привилегиями).
    
```
Connect-MsolService
```

В диалоговом окне **входа в учетную запись** введите работы Office 365 или школа имя учетной записи и пароль и нажмите кнопку **ОК**.

При использовании многофакторной проверкой Подлинности следуйте инструкциям в диалоговых окнах дополнительные, чтобы предоставить дополнительные сведения о проверке подлинности, такие как код подтверждения.

>[!Tip]
>Для подключения к Office 365 Германия видеть [подключение к Германии Azure с помощью PowerShell](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps).
>
    
### <a name="how-do-you-know-this-worked"></a>Как убедиться, что все получилось?

Если не возникло никаких ошибок, значит, подключение выполнено успешно. Чтобы выполнить быструю проверку, запустите командлет Office 365:, например **Get-MsolUser**, и просмотрите результаты.
  
Если возникают ошибки, просмотрите список возможных причин:
  
- **Распространенная проблема — неправильный пароль.**. Еще раз выполните шаг 3. Будьте особенно внимательны при вводе имени пользователя и пароля.
    
- * *Требует Microsoft Azure модуль Active Directory для Windows PowerShell, Microsoft .NET Framework 3.5.* x * включен на компьютере **. Вероятно, что на компьютере установлена более новой версии (например, 4 или 4.5.* x *), но обратной совместимости с предыдущими версиями платформы .NET Framework можно включить или отключить. Дополнительные сведения в следующих разделах:
    
  - [Включение .NET Framework 3.5 с помощью мастера добавления ролей и функций](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Windows Server 2012 или Windows Server 2012 R2)
    
  - [Не удается открыть модуль Azure Active Directory для Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) (Windows 7 или Windows Server 2008 R2)

  - Windows 10, Windows 8.1 и Windows 8 содержатся в разделе [Установка .NET Framework 3.5 на Windows 10, Windows 8.1 и Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
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

