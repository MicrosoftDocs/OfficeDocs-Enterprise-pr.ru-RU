---
title: "Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: "Сводка.PowerShell в Office 365 позволяет назначать индивидуальные параметры связи с политиками Skype для бизнеса Online."
ms.openlocfilehash: 91916b41ba420a204ecabb27eea2e451a91f6f25
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell

 **Сводка:** Использование Office 365 PowerShell для назначения пользователя параметры связи с Скайп для бизнеса в Интернет политик.
  
PowerShell в Office 365 позволяет эффективно назначать индивидуальные параметры связи с политиками Skype для бизнеса Online.
  
## <a name="before-you-begin"></a>Перед началом работы

Чтобы получить настройки для выполнения команд, воспользуйтесь приведенными ниже инструкциями (пропустите выполненные ранее шаги).
  
1. Скачайте и установите [ модуль соединителя с Skype для бизнеса Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366).
    
2. Откройте командную строку Windows PowerShell и выполните указанные команды: 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
При поступлении соответствующего запроса системы введите имя и пароль учетной записи администратора Skype для бизнеса Online.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Обновление параметров внешней связи для учетной записи пользователя

Предположим, вы решили изменить параметры внешней связи для учетной записи пользователя. Например, необходимо разрешить Семену связываться с федеративными пользователями (задав для свойства EnableFederationAccess значение True) и запретить обмениваться данными с пользователями Windows Live (установив для политики EnablePublicCloudAccess значение False). Для этого необходимо выполнить два действия:
  
1. найти политику внешнего доступа, которая отвечает нашим критериям;
    
2. назначить эту политику внешнего доступа пользователю Семену.
    
> [!NOTE]
>  Не удается создать пользовательскую политику все собственные. Вот так, как Скайп для бизнеса в Интернет не позволяет создавать пользовательские политики. Вместо этого необходимо назначить одну из политик, которые были созданы специально для Office 365. Предварительно созданных политик включают: 4 различные клиентские политики, политик 224 различные конференц-связи, 5 различных абонентских групп, 5 разных политик внешнего доступа, политики размещенной голосовой почты; 1 и 4 различных политики голосовых служб.
  
Как узнать, какую политику внешнего доступа нужно назначить пользователю Семену? Приведенная ниже команда возвращает все политики внешнего доступа, в которых для свойства EnableFederationAccess и политики EnablePublicCloudAccess заданы значения True и False соответственно.
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Что означает команда является возврата всех политик, соответствующие двум критериям: свойство EnableFederationAccess задано значение True, а политики EnablePublicCloudAccess установлено значение False. В свою очередь эта команда возвращает одну политику, которая отвечает нашим критериям (FederationOnly). Ниже приведен пример:
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> Идентификатор политики выглядит как Tag:FederationOnly. Как оказывается, префикс Tag:  это пережиток ранних предварительных выпусков Microsoft Lync 2013. При назначении политики пользователям следует удалить префикс Tag: и использовать только имя политики: FederationOnly. 
  
Теперь мы знаем, какую политику назначить пользователю Семену, и сделаем это с помощью командлета [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974). Ниже приведен пример.
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Назначить политику очень просто: нужно всего лишь указать идентификатор пользователя и имя назначаемой политики. 
  
Что касается политик и их назначений, можно одновременно работать с несколькими учетными записями пользователей. Например, предположим, что вам нужен список всех пользователей, которым разрешено обмениваться данными с федеративными партнерами и пользователями Windows Live. Мы уже знаем, что этим пользователям назначена политика доступа к внешним пользователям FederationAndPICDefault. Благодаря этому мы можем вернуть список всех этих пользователей, выполнив одну простую команду, которая приведена ниже.
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Другими словами, отобразятся все пользователи, для свойства ExternalAccessPolicy которых задано значение FederationAndPICDefault. (Чтобы ограничить объем сведений, которые появляются на экране, используйте командлет Select-Object для показа только отображаемого имени каждого пользователя.) 
  
Для настройки всех учетных записей пользователей на применение одной политики воспользуйтесь следующей командой:
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

С помощью командлета Get-CsOnlineUser эта команда возвращает коллекцию всех пользователей с включенной поддержкой Lync, затем передает эти сведения командлету Grant-CsExternalAccessPolicy, который назначает политику FederationAndPICDefault каждому пользователю в коллекции.
  
В качестве дополнительного примера предположим, что вы ранее назначили пользователю Семену политику FederationAndPICDefault, но передумали и хотите управлять им с помощью глобальной политики внешнего доступа. Глобальную политику нельзя явно назначить какому-либо пользователю. Она используется только в тех случаях, когда пользователю не назначена индивидуальная политика. Таким образом, чтобы пользователем Семеном управляла глобальная политика, необходимо  *отменить*  все ранее назначенные ему индивидуальные политики. Ниже приведен пример соответствующей команды.
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Эта команда задает значение Null ($Null) для имени политики внешнего доступа, назначенной Семену. Значение Null означает "ничего". Другими словами, Семену не назначена ни одна политика внешнего доступа. Если пользователю не назначена ни одна политика внешнего доступа, для управления им используется глобальная политика.
  
Чтобы отключить учетную запись пользователя, с помощью Windows PowerShell, используйте командлеты Azure Active Directory для удаления Скайп Семена для бизнеса в Интернет лицензии. Дополнительные сведения можно [отключить доступ к службам с помощью Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>See also

#### 

[Управление Skype для бизнеса Online с помощью Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

