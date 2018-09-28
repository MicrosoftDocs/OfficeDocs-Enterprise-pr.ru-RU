---
title: Управление Skype для бизнеса Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Сводка: в этой статье рассказывается, как использовать PowerShell в Office 365 для управления параметрами политик, индивидуальных политик для пользователей и собраний в Skype для бизнеса Online.'
ms.openlocfilehash: a91803316972337aa31e2b979f841ac1cfbe8566
ms.sourcegitcommit: 053db5479f93478a65d4c36ffe44c6a7bcb60e3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "23965196"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Управление Skype для бизнеса Online с помощью Office 365 PowerShell

 **Сводка.** Управляйте политиками и настройками собраний Skype для бизнеса Online, используя PowerShell для Office 365.
  
Один из основных задач любой Скайп для бизнеса в Интернет администратор Управление политиками. Несмотря на то, что можно выполнить некоторые из этих задач в центре администрирования Office 365, другие задачи, намного быстрее и проще в Office 365 PowerShell. 

## <a name="before-you-start"></a>Перед началом работы

Загрузить и установить [Скайп для модуля Business Online Connector](https://www.microsoft.com/en-us/download/details.aspx?id=39366)и при появлении соответствующего запроса перезагрузите компьютер.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Подключение через Скайп Business Online имя учетной записи администратора и пароля

1. Откройте командную строку Windows PowerShell и выполните указанные команды: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. В диалоговом окне **Запрос учетных данных Windows PowerShell** введите вашей Скайп для бизнеса в Интернет имя учетной записи администратора и пароль и нажмите кнопку **ОК**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Подключение через Скайп для бизнеса в Интернет учетной записи администратора с многофакторной проверкой подлинности

1. Откройте командную строку Windows PowerShell и выполните указанные команды:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. При появлении запроса с помощью команды **New-CsOnlineSession** введите вашей Скайп для бизнеса в Интернет имя учетной записи администратора.

3. В диалоговом окне **входа в свою учетную запись** введите ваше Скайп для бизнеса в Интернет пароль администратора и нажмите кнопку **Вход**.

4. Следуйте инструкциям в диалоговом окне **входа в учетную запись** для обеспечения проверки подлинности на дополнительные сведения, такие как код подтверждения и нажмите кнопку **Проверить**.

Дополнительные сведения приведены в следующих разделах:
  
- [Управление политиками Skype для бизнеса Online с помощью Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>См. также

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

[Скайп для ссылок на командлета PowerShell бизнеса](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

