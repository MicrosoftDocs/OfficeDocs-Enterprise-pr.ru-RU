---
title: Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: Сводка.PowerShell в Office 365 позволяет назначать индивидуальные параметры связи с политиками Skype для бизнеса Online.
ms.openlocfilehash: 615deca2790e206e6cf117283321307aa01eac74
ms.sourcegitcommit: f2aefbc2dbbe969fea9db3a4c558651496532413
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2020
ms.locfileid: "43146814"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell

PowerShell в Office 365 позволяет эффективно назначать индивидуальные параметры связи с политиками Skype для бизнеса Online.
  
## <a name="before-you-begin"></a>Перед началом работы

Чтобы получить настройки для выполнения команд, воспользуйтесь приведенными ниже инструкциями (пропустите выполненные ранее шаги).
  
1. Скачайте и установите [ модуль соединителя с Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366).
    
2. Откройте командную строку Windows PowerShell и выполните указанные команды: 
    
```powershell
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
>  Вам не удастся создать полностью настраиваемую политику. Это связано с тем, что в Skype для бизнеса Online нельзя создавать собственные политики. Вместо этого следует назначить одну из политик, созданных специально для Office 365. К этим политикам относятся: 4 клиентские политики, 224 политики в отношении конференций, 5 абонентских групп, 5 политик внешнего доступа, 1 политика размещенной голосовой почты и 4 политики голосовой связи.
  
Как узнать, какую политику внешнего доступа нужно назначить пользователю Семену? Приведенная ниже команда возвращает все политики внешнего доступа, в которых для свойства EnableFederationAccess и политики EnablePublicCloudAccess заданы значения True и False соответственно.
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Команда возвращает все политики, соответствующие двум условиям: для свойства EnableFederationAccess задано значение True, а для политики EnablePublicCloudAccess — значение False. В свою очередь, эта команда возвращает одну политику, которая отвечает нашим условиям (FederationOnly). Ниже приведен пример.
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> Идентификатор политики выглядит как Tag:FederationOnly. Как оказывается, префикс Tag: — это пережиток ранних предварительных выпусков Microsoft Lync 2013. При назначении политики пользователям следует удалить префикс Tag: и использовать только имя политики: FederationOnly. 
  
Теперь мы знаем, какую политику назначить пользователю Семену, и сделаем это с помощью командлета [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974). Ниже приведен пример.
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Назначить политику очень просто: нужно всего лишь указать идентификатор пользователя и имя назначаемой политики. 
  
Что касается политик и их назначений, можно одновременно работать с несколькими учетными записями пользователей. Например, предположим, что вам нужен список всех пользователей, которым разрешено обмениваться данными с федеративными партнерами и пользователями Windows Live. Мы уже знаем, что этим пользователям назначена политика доступа к внешним пользователям FederationAndPICDefault. Благодаря этому мы можем вернуть список всех этих пользователей, выполнив одну простую команду, которая приведена ниже.
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Другими словами, отобразятся все пользователи, для свойства ExternalAccessPolicy которых задано значение FederationAndPICDefault. (Чтобы ограничить объем сведений, которые появляются на экране, используйте командлет Select-Object для показа только отображаемого имени каждого пользователя.) 
  
Для настройки всех учетных записей пользователей на применение одной политики воспользуйтесь следующей командой:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

С помощью командлета Get-CsOnlineUser эта команда возвращает коллекцию всех пользователей с включенной поддержкой Lync, затем передает эти сведения командлету Grant-CsExternalAccessPolicy, который назначает политику FederationAndPICDefault каждому пользователю в коллекции.
  
В качестве дополнительного примера предположим, что вы ранее назначили пользователю Семену политику FederationAndPICDefault, но передумали и хотите управлять им с помощью глобальной политики внешнего доступа. Глобальную политику нельзя явно назначить какому-либо пользователю. Она используется только в тех случаях, когда пользователю не назначена индивидуальная политика. Таким образом, чтобы пользователем Семеном управляла глобальная политика, необходимо  *отменить*  все ранее назначенные ему индивидуальные политики. Ниже приведен пример соответствующей команды.
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Эта команда задает значение Null ($Null) для имени политики внешнего доступа, назначенной Семену. Значение Null означает "ничего". Другими словами, Семену не назначена ни одна политика внешнего доступа. Если пользователю не назначена ни одна политика внешнего доступа, для управления им используется глобальная политика.
  
Чтобы отключить учетную запись пользователя с помощью Windows PowerShell, удалите лицензию пользователя Alex на Skype Online для бизнеса, используя командлеты Azure Active Directory. Дополнительные сведения см. в статье [Отключение доступа к службам с помощью PowerShell для Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md).

## <a name="managing-large-numbers-of-users"></a>Управление большим количеством пользователей

Для управления большим количеством пользователей (1000 или более) необходимо выполнить пакетную команду с помощью блока сценария с помощью командлета [Invoke-Command](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) .  В предыдущих примерах при каждом запуске командлета необходимо настроить вызов, а затем дождаться результата перед его отправкой.  При использовании блока сценария это позволяет выполнять командлеты удаленно, а после завершения отправлять данные обратно. 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

Пользователи смогут найти 500 пользователей за раз без политики клиента. Он предоставит им политику клиента "Клиентполициноимурл" и политику внешнего доступа "Федератионандпикдефаулт". Результаты группируются в группы 50, а каждый пакет 50 отправляется на удаленный компьютер.
  
## <a name="see-also"></a>См. также

[Управление Skype для бизнеса Online с помощью Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)
