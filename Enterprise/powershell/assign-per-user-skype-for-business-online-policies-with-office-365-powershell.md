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
ms.openlocfilehash: 89b3ab5ce571c9812e2b4f3d3aef7066a7babb08
ms.sourcegitcommit: 0c2d4cfb4d1b21ea93bcc6eb52421548db34b1e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2020
ms.locfileid: "44374448"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="d5e9c-103">Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5e9c-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="d5e9c-104">PowerShell в Office 365 позволяет эффективно назначать индивидуальные параметры связи с политиками Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-104">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d5e9c-105">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="d5e9c-105">Before you begin</span></span>

<span data-ttu-id="d5e9c-106">Чтобы получить настройки для выполнения команд, воспользуйтесь приведенными ниже инструкциями (пропустите выполненные ранее шаги).</span><span class="sxs-lookup"><span data-stu-id="d5e9c-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="d5e9c-107">Скачайте и установите [ модуль соединителя с Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="d5e9c-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="d5e9c-108">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="d5e9c-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="d5e9c-109">При поступлении соответствующего запроса системы введите имя и пароль учетной записи администратора Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="d5e9c-110">Обновление параметров внешней связи для учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="d5e9c-110">Updating external communication settings for a user account</span></span>

<span data-ttu-id="d5e9c-p101">Предположим, вы решили изменить параметры внешней связи для учетной записи пользователя. Например, необходимо разрешить Семену связываться с федеративными пользователями (задав для свойства EnableFederationAccess значение True) и запретить обмениваться данными с пользователями Windows Live (установив для политики EnablePublicCloudAccess значение False). Для этого необходимо выполнить два действия:</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="d5e9c-114">найти политику внешнего доступа, которая отвечает нашим критериям;</span><span class="sxs-lookup"><span data-stu-id="d5e9c-114">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="d5e9c-115">назначить эту политику внешнего доступа пользователю Семену.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-115">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="d5e9c-p102">Вам не удастся создать полностью настраиваемую политику. Это связано с тем, что в Skype для бизнеса Online нельзя создавать собственные политики. Вместо этого следует назначить одну из политик, созданных специально для Office 365. К этим политикам относятся: 4 клиентские политики, 224 политики в отношении конференций, 5 абонентских групп, 5 политик внешнего доступа, 1 политика размещенной голосовой почты и 4 политики голосовой связи.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="d5e9c-p103">Как узнать, какую политику внешнего доступа нужно назначить пользователю Семену? Приведенная ниже команда возвращает все политики внешнего доступа, в которых для свойства EnableFederationAccess и политики EnablePublicCloudAccess заданы значения True и False соответственно.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="d5e9c-p104">Команда возвращает все политики, соответствующие двум условиям: для свойства EnableFederationAccess задано значение True, а для политики EnablePublicCloudAccess — значение False. В свою очередь, эта команда возвращает одну политику, которая отвечает нашим условиям (FederationOnly). Ниже приведен пример.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy that meets our criteria (FederationOnly). Here is an example:</span></span>
  
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
> <span data-ttu-id="d5e9c-p105">Идентификатор политики выглядит как Tag:FederationOnly. Как оказывается, префикс Tag: — это пережиток ранних предварительных выпусков Microsoft Lync 2013. При назначении политики пользователям следует удалить префикс Tag: и использовать только имя политики: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="d5e9c-p106">Теперь мы знаем, какую политику назначить пользователю Семену, и сделаем это с помощью командлета [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974). Ниже приведен пример.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="d5e9c-130">Назначить политику очень просто: нужно всего лишь указать идентификатор пользователя и имя назначаемой политики.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-130">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="d5e9c-p107">Что касается политик и их назначений, можно одновременно работать с несколькими учетными записями пользователей. Например, предположим, что вам нужен список всех пользователей, которым разрешено обмениваться данными с федеративными партнерами и пользователями Windows Live. Мы уже знаем, что этим пользователям назначена политика доступа к внешним пользователям FederationAndPICDefault. Благодаря этому мы можем вернуть список всех этих пользователей, выполнив одну простую команду, которая приведена ниже.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="d5e9c-p108">Другими словами, отобразятся все пользователи, для свойства ExternalAccessPolicy которых задано значение FederationAndPICDefault. (Чтобы ограничить объем сведений, которые появляются на экране, используйте командлет Select-Object для показа только отображаемого имени каждого пользователя.)</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="d5e9c-138">Для настройки всех учетных записей пользователей на применение одной политики воспользуйтесь следующей командой:</span><span class="sxs-lookup"><span data-stu-id="d5e9c-138">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="d5e9c-139">С помощью командлета Get-CsOnlineUser эта команда возвращает коллекцию всех пользователей с включенной поддержкой Lync, затем передает эти сведения командлету Grant-CsExternalAccessPolicy, который назначает политику FederationAndPICDefault каждому пользователю в коллекции.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-139">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="d5e9c-p109">В качестве дополнительного примера предположим, что вы ранее назначили пользователю Семену политику FederationAndPICDefault, но передумали и хотите управлять им с помощью глобальной политики внешнего доступа. Глобальную политику нельзя явно назначить какому-либо пользователю. Она используется только в тех случаях, когда пользователю не назначена индивидуальная политика. Таким образом, чтобы пользователем Семеном управляла глобальная политика, необходимо  *отменить*  все ранее назначенные ему индивидуальные политики. Ниже приведен пример соответствующей команды.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="d5e9c-p110">Эта команда задает значение Null ($Null) для имени политики внешнего доступа, назначенной Семену. Значение Null означает "ничего". Другими словами, Семену не назначена ни одна политика внешнего доступа. Если пользователю не назначена ни одна политика внешнего доступа, для управления им используется глобальная политика.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="d5e9c-p111">Чтобы отключить учетную запись пользователя с помощью Windows PowerShell, удалите лицензию пользователя Alex на Skype Online для бизнеса, используя командлеты Azure Active Directory. Дополнительные сведения см. в статье [Отключение доступа к службам с помощью PowerShell для Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d5e9c-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="d5e9c-151">Управление большим количеством пользователей</span><span class="sxs-lookup"><span data-stu-id="d5e9c-151">Managing large numbers of users</span></span>

<span data-ttu-id="d5e9c-152">Для управления большим количеством пользователей (1000 или более) необходимо выполнить пакетную команду с помощью блока сценария с помощью командлета [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) .</span><span class="sxs-lookup"><span data-stu-id="d5e9c-152">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="d5e9c-153">В предыдущих примерах при каждом запуске командлета необходимо настроить вызов, а затем дождаться результата перед его отправкой.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-153">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="d5e9c-154">При использовании блока сценария это позволяет выполнять командлеты удаленно, а после завершения отправлять данные обратно.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-154">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

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

<span data-ttu-id="d5e9c-155">Пользователи смогут найти 500 пользователей за раз без политики клиента.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-155">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="d5e9c-156">Он предоставит им политику клиента "Клиентполициноимурл" и политику внешнего доступа "Федератионандпикдефаулт".</span><span class="sxs-lookup"><span data-stu-id="d5e9c-156">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="d5e9c-157">Результаты группируются в группы 50, а каждый пакет 50 отправляется на удаленный компьютер.</span><span class="sxs-lookup"><span data-stu-id="d5e9c-157">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d5e9c-158">См. также</span><span class="sxs-lookup"><span data-stu-id="d5e9c-158">See also</span></span>

[<span data-ttu-id="d5e9c-159">Управление Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5e9c-159">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="d5e9c-160">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="d5e9c-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d5e9c-161">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5e9c-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
