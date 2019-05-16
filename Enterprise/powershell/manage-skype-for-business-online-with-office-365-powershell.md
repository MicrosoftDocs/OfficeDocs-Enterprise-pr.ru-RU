---
title: Управление Skype для бизнеса Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Сводка: в этой статье рассказывается, как использовать PowerShell в Office 365 для управления параметрами политик, индивидуальных политик для пользователей и собраний в Skype для бизнеса Online.'
ms.openlocfilehash: 33c7247686cc8eb308b8db6d4900c89f693004fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068735"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Управление Skype для бизнеса Online с помощью Office 365 PowerShell

 **Сводка.** Управляйте политиками и настройками собраний Skype для бизнеса Online, используя PowerShell для Office 365.
  
Одной из основных задач администратора Skype для бизнеса Online является Управление политиками. Хотя вы можете выполнить некоторые из этих задач в центре администрирования Office 365, другие задачи будут значительно быстрее и проще в Office 365 PowerShell. 

## <a name="before-you-start"></a>Перед началом работы

Скачайте и установите [модуль соединителя Skype для бизнеса Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366), а затем перезагрузите компьютер при появлении соответствующего запроса.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Подключение с помощью имени и пароля учетной записи администратора Skype для бизнеса Online

1. Откройте командную строку Windows PowerShell и выполните указанные команды: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. В диалоговом окне **запрос учетных данных Windows PowerShell** введите имя и пароль учетной записи администратора Skype для бизнеса Online, а затем нажмите кнопку **ОК**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Подключение с использованием учетной записи администратора Skype для бизнеса Online с многофакторной проверкой подлинности

1. Откройте командную строку Windows PowerShell и выполните указанные команды:

  ```
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

