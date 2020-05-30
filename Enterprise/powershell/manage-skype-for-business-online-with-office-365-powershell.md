---
title: Управление Skype для бизнеса Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/28/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Сводка: в этой статье рассказывается, как использовать PowerShell в Office 365 для управления параметрами политик, индивидуальных политик для пользователей и собраний в Skype для бизнеса Online.'
ms.openlocfilehash: f1a5df3802d43755e81465743b81c5fbb9fff7e0
ms.sourcegitcommit: 6c7cc6aca8713e280ae6ff51226dde9db4497401
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "44415941"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Управление Skype для бизнеса Online с помощью Office 365 PowerShell

Одной из основных задач администратора Skype для бизнеса Online является Управление политиками. Вы можете выполнить некоторые из указанных ниже задач в Центре администрирования Microsoft 365, но остальные задачи гораздо быстрее и проще выполнить с помощью PowerShell в Office 365. 

## <a name="before-you-start"></a>Перед началом работы

Скачайте и установите [модуль соединителя Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366), а затем перезагрузите компьютер.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Подключение с помощью имени и пароля учетной записи администратора Skype для бизнеса Online

1. Откройте командную строку Windows PowerShell и выполните указанные команды: 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. В диалоговом окне **запрос учетных данных Windows PowerShell** введите имя и пароль учетной записи администратора Skype для бизнеса Online, а затем нажмите кнопку **ОК**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>Подключение с помощью учетной записи администратора Skype для бизнеса Online с многофакторной проверкой подлинности

1. Откройте командную строку Windows PowerShell и выполните указанные команды:

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Когда появится команда **New-CsOnlineSession** , введите имя учетной записи администратора Skype для бизнеса Online.

3. В диалоговом окне **Вход в учетную запись** введите пароль администратора Skype для бизнеса Online и нажмите кнопку **войти**.

4. Следуйте инструкциям в диалоговом окне **Вход в учетную запись** , чтобы предоставить дополнительные сведения о проверке подлинности, например код подтверждения, и нажмите кнопку **проверить**.

Дополнительную информацию см. в следующих статьях:
  
- [Управление политиками Skype для бизнеса Online с помощью Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>См. также

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

[Справочные материалы по командлетам PowerShell в Skype для бизнеса](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

