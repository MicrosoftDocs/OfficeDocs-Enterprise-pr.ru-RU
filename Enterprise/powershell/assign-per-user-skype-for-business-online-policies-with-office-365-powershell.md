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
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: Сводка.PowerShell в Office 365 позволяет назначать индивидуальные параметры связи с политиками Skype для бизнеса Online.
ms.openlocfilehash: 2252a6df4298bb36a669404aefac3b14eaa23b7f
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031044"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="1c1e7-103">Назначение индивидуальных политик для Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c1e7-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="1c1e7-104">**Сводка.** Назначайте индивидуальные параметры связи и политики Skype для бизнеса Online, используя PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-104">**Summary:** Use Office 365 PowerShell to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
<span data-ttu-id="1c1e7-105">PowerShell в Office 365 позволяет эффективно назначать индивидуальные параметры связи с политиками Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-105">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="1c1e7-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="1c1e7-106">Before you begin</span></span>

<span data-ttu-id="1c1e7-107">Чтобы получить настройки для выполнения команд, воспользуйтесь приведенными ниже инструкциями (пропустите выполненные ранее шаги).</span><span class="sxs-lookup"><span data-stu-id="1c1e7-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="1c1e7-108">Скачайте и установите [ модуль соединителя с Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="1c1e7-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="1c1e7-109">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="1c1e7-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
<span data-ttu-id="1c1e7-110">При поступлении соответствующего запроса системы введите имя и пароль учетной записи администратора Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="1c1e7-111">Обновление параметров внешней связи для учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="1c1e7-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="1c1e7-p101">Предположим, вы решили изменить параметры внешней связи для учетной записи пользователя. Например, необходимо разрешить Семену связываться с федеративными пользователями (задав для свойства EnableFederationAccess значение True) и запретить обмениваться данными с пользователями Windows Live (установив для политики EnablePublicCloudAccess значение False). Для этого необходимо выполнить два действия:</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="1c1e7-115">найти политику внешнего доступа, которая отвечает нашим критериям;</span><span class="sxs-lookup"><span data-stu-id="1c1e7-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="1c1e7-116">назначить эту политику внешнего доступа пользователю Семену.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-116">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="1c1e7-p102">Вам не удастся создать полностью настраиваемую политику. Это связано с тем, что в Skype для бизнеса Online нельзя создавать собственные политики. Вместо этого следует назначить одну из политик, созданных специально для Office 365. К этим политикам относятся: 4 клиентские политики, 224 политики в отношении конференций, 5 абонентских групп, 5 политик внешнего доступа, 1 политика размещенной голосовой почты и 4 политики голосовой связи.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="1c1e7-p103">Как узнать, какую политику внешнего доступа нужно назначить пользователю Семену? Приведенная ниже команда возвращает все политики внешнего доступа, в которых для свойства EnableFederationAccess и политики EnablePublicCloudAccess заданы значения True и False соответственно.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="1c1e7-p104">Команда возвращает все политики, соответствующие двум условиям: для свойства EnableFederationAccess задано значение True, а для политики EnablePublicCloudAccess — значение False. В свою очередь, эта команда возвращает одну политику, которая отвечает нашим условиям (FederationOnly). Ниже приведен пример.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy that meets our criteria (FederationOnly). Here is an example:</span></span>
  
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
> <span data-ttu-id="1c1e7-p105">Идентификатор политики выглядит как Tag:FederationOnly. Как оказывается, префикс Tag: — это пережиток ранних предварительных выпусков Microsoft Lync 2013. При назначении политики пользователям следует удалить префикс Tag: и использовать только имя политики: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="1c1e7-p106">Теперь мы знаем, какую политику назначить пользователю Семену, и сделаем это с помощью командлета [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974). Ниже приведен пример.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="1c1e7-131">Назначить политику очень просто: нужно всего лишь указать идентификатор пользователя и имя назначаемой политики.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-131">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="1c1e7-p107">Что касается политик и их назначений, можно одновременно работать с несколькими учетными записями пользователей. Например, предположим, что вам нужен список всех пользователей, которым разрешено обмениваться данными с федеративными партнерами и пользователями Windows Live. Мы уже знаем, что этим пользователям назначена политика доступа к внешним пользователям FederationAndPICDefault. Благодаря этому мы можем вернуть список всех этих пользователей, выполнив одну простую команду, которая приведена ниже.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="1c1e7-p108">Другими словами, отобразятся все пользователи, для свойства ExternalAccessPolicy которых задано значение FederationAndPICDefault. (Чтобы ограничить объем сведений, которые появляются на экране, используйте командлет Select-Object для показа только отображаемого имени каждого пользователя.)</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="1c1e7-139">Для настройки всех учетных записей пользователей на применение одной политики воспользуйтесь следующей командой:</span><span class="sxs-lookup"><span data-stu-id="1c1e7-139">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="1c1e7-140">С помощью командлета Get-CsOnlineUser эта команда возвращает коллекцию всех пользователей с включенной поддержкой Lync, затем передает эти сведения командлету Grant-CsExternalAccessPolicy, который назначает политику FederationAndPICDefault каждому пользователю в коллекции.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-140">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="1c1e7-p109">В качестве дополнительного примера предположим, что вы ранее назначили пользователю Семену политику FederationAndPICDefault, но передумали и хотите управлять им с помощью глобальной политики внешнего доступа. Глобальную политику нельзя явно назначить какому-либо пользователю. Она используется только в тех случаях, когда пользователю не назначена индивидуальная политика. Таким образом, чтобы пользователем Семеном управляла глобальная политика, необходимо  *отменить*  все ранее назначенные ему индивидуальные политики. Ниже приведен пример соответствующей команды.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="1c1e7-p110">Эта команда задает значение Null ($Null) для имени политики внешнего доступа, назначенной Семену. Значение Null означает "ничего". Другими словами, Семену не назначена ни одна политика внешнего доступа. Если пользователю не назначена ни одна политика внешнего доступа, для управления им используется глобальная политика.</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="1c1e7-p111">Чтобы отключить учетную запись пользователя с помощью Windows PowerShell, удалите лицензию пользователя Alex на Skype Online для бизнеса, используя командлеты Azure Active Directory. Дополнительные сведения см. в статье [Отключение доступа к службам с помощью PowerShell для Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1c1e7-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1c1e7-152">См. также</span><span class="sxs-lookup"><span data-stu-id="1c1e7-152">See also</span></span>

#### 

[<span data-ttu-id="1c1e7-153">Управление Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c1e7-153">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="1c1e7-154">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="1c1e7-154">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1c1e7-155">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c1e7-155">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

