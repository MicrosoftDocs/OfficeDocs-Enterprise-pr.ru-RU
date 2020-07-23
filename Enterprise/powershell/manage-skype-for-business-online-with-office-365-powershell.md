---
title: Управление Skype для бизнеса Online с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Сводка: использование PowerShell для Microsoft 365 для управления политиками Skype для бизнеса Online, политиками для отдельных пользователей и параметрами собраний.'
ms.openlocfilehash: f66b3186a5b29bbf0756a629b85c626caf2c1e36
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230445"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Управление Skype для бизнеса Online с помощью PowerShell

*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*

Одной из основных задач администратора Skype для бизнеса Online является Управление политиками. Несмотря на то, что вы можете выполнить некоторые из этих задач в центре администрирования Microsoft 365, другие задачи выполняются значительно быстрее и проще в PowerShell. 

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
  
- [Управление политиками Skype для бизнеса Online с помощью PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Назначение политик Skype для бизнеса Online для отдельных пользователей с помощью PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>См. также

[Управление Microsoft 365 с помощью PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с PowerShell для Microsoft 365](getting-started-with-office-365-powershell.md)

[Справочные материалы по командлетам PowerShell в Skype для бизнеса](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

