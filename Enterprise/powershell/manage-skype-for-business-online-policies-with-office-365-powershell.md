---
title: Управление политиками Skype для бизнеса Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: Сводка.PowerShell в Office 365 позволяет управлять свойствами учетной записи пользователя Skype для бизнеса Online с политиками.
ms.openlocfilehash: 51e402922b2a357ef29e9b2628eb25fc252e5437
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031734"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="73f5f-103">Управление политиками Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="73f5f-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="73f5f-104">**Сводка.** Управляйте свойствами учетной записи пользователя Skype для бизнеса Online и политиками, используя PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="73f5f-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="73f5f-105">Для управления свойствами учетной записи пользователя для Skype для бизнеса Online, необходимо указать их в качестве параметров политик с помощью PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="73f5f-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="73f5f-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="73f5f-106">Before you begin</span></span>

<span data-ttu-id="73f5f-107">Чтобы получить настройки для выполнения команд, воспользуйтесь приведенными ниже инструкциями (пропустите выполненные ранее шаги).</span><span class="sxs-lookup"><span data-stu-id="73f5f-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="73f5f-108">Скачайте и установите [ модуль соединителя с Skype для бизнеса Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="73f5f-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="73f5f-109">Откройте командную строку Windows PowerShell и выполните указанные команды:</span><span class="sxs-lookup"><span data-stu-id="73f5f-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="73f5f-110">При поступлении соответствующего запроса системы введите имя и пароль учетной записи администратора Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="73f5f-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="73f5f-111">Управление политиками учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="73f5f-111">Manage user account policies</span></span>

<span data-ttu-id="73f5f-p101">Многие свойства учетной записи пользователя Skype для бизнеса Online настраиваются с помощью политик. Политики  это просто коллекции параметров, которые можно применить к одному или нескольким пользователям. Чтобы рассмотреть настройки политики, можно воспользоваться приведенной ниже командой для политики FederationAndPICDefault в качестве примера:</span><span class="sxs-lookup"><span data-stu-id="73f5f-p101">Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="73f5f-115">В ответ вы должны получить что-то вроде этого:</span><span class="sxs-lookup"><span data-stu-id="73f5f-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="73f5f-p102">В этом примере значения в этой политике определяют, что может или не может делать использование, когда речь идет о взаимодействии с федеративными пользователями. Например, свойству Енаблеаутсидеакцесс должно быть присвоено значение true, чтобы пользователь мог общаться с пользователями, не входящими в организацию. Обратите внимание, что это свойство не отображается в центре администрирования Microsoft 365. Вместо этого для свойства автоматически задается значение true или false в зависимости от того, какие параметры выбраны. Два других свойства интересов:</span><span class="sxs-lookup"><span data-stu-id="73f5f-p102">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users. For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization. Note that this property does not appear in the Microsoft 365 admin center. Instead, the property is automatically set to True or False based on the other selections that you make. The other two properties of interest are:</span></span>
  
- <span data-ttu-id="73f5f-121">Свойство **EnableFederationAccess** указывает, может ли пользователь обмениваться данными с пользователями из федеративных доменов.</span><span class="sxs-lookup"><span data-stu-id="73f5f-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="73f5f-122">Свойство **EnablePublicCloudAccess** указывает, может ли пользователь обмениваться данными с пользователями Windows Live.</span><span class="sxs-lookup"><span data-stu-id="73f5f-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="73f5f-p103">Следовательно, вы не изменяете свойства учетной записи пользователя, связанные с федерацией (например, **Set-CsUser -EnableFederationAccess $True**). Вместо этого вы назначаете пользователю политику внешнего доступа с предварительно настроенными значениями необходимых свойств. Чтобы пользователь смог обмениваться данными с федеративными пользователями и пользователями Windows Live, ему нужно назначить политику, разрешающую такой обмен данными.</span><span class="sxs-lookup"><span data-stu-id="73f5f-p103">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="73f5f-126">Чтобы узнать, может ли пользователь обмениваться данными с пользователями вне организации, необходимо выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="73f5f-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="73f5f-127">Определить, какая политика внешнего доступа назначена этому пользователю.</span><span class="sxs-lookup"><span data-stu-id="73f5f-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="73f5f-128">Определить, какие возможности разрешает или запрещает эта политика.</span><span class="sxs-lookup"><span data-stu-id="73f5f-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="73f5f-129">Для этого можно воспользоваться указанной командой.</span><span class="sxs-lookup"><span data-stu-id="73f5f-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="73f5f-130">Эта команда находит политику, назначенную пользователю, а затем находит возможности, которые включены или отключены в этой политике.</span><span class="sxs-lookup"><span data-stu-id="73f5f-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="73f5f-131">Для управления политиками Skype для бизнеса Online с помощью PowerShell обратитесь к командлетам для:</span><span class="sxs-lookup"><span data-stu-id="73f5f-131">To manage Skype for Business Online policies with PowerShell, see the cmdlets for:</span></span>

- <span data-ttu-id="73f5f-132">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets) (Политика клиента).</span><span class="sxs-lookup"><span data-stu-id="73f5f-132">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span></span>
- <span data-ttu-id="73f5f-133">[Политика конференц-связи](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets),</span><span class="sxs-lookup"><span data-stu-id="73f5f-133">[Conferencing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span></span>
- <span data-ttu-id="73f5f-134">[Политика для мобильных устройств](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="73f5f-134">[Mobile policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span></span>
- <span data-ttu-id="73f5f-135">[Политика сетевой голосовой почты](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="73f5f-135">[Online Voicemail policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span></span>
- <span data-ttu-id="73f5f-136">[Политика маршрутизации голосовой связи](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="73f5f-136">[Voice Routing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span></span>


> [!NOTE]
> <span data-ttu-id="73f5f-p104">Абонентская группа Skype для бизнеса Online  это политика во всех отношениях, кроме имени. Название "абонентская группа" выбрано вместо других названий (скажем, "политика набора") для обеспечения обратной совместимости с Office Communications Server и Exchange.</span><span class="sxs-lookup"><span data-stu-id="73f5f-p104">A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="73f5f-139">Например, чтобы просмотреть все доступные политики голосовой связи, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="73f5f-139">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="73f5f-p105">Будет возвращен список всех доступных политик голосовой связи. Однако имейте в виду, что пользователям нельзя назначить некоторые политики. Это связано с различными ограничениями в отношении [места лицензирования и использования](https://msdn.microsoft.com/library/azure/dn194136.aspx). Чтобы узнать, какие политики внешнего доступа и конференций можно назначить пользователю, выполните команды, похожие на следующие:</span><span class="sxs-lookup"><span data-stu-id="73f5f-p105">That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](https://msdn.microsoft.com/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="73f5f-p106">Параметр ApplicableTo ограничивает данные, возвращаемые политиками, которые можно назначить указанному пользователю (например, Семену Маслову). В зависимости от ограничений в отношении лицензирования и места использования он может представлять подмножество всех доступных политик.</span><span class="sxs-lookup"><span data-stu-id="73f5f-p106">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="73f5f-146">В некоторых случаях свойства политик не используются с Office 365, а другими могут управлять только сотрудники службы поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="73f5f-146">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="73f5f-p107">С Skype для бизнеса Online для управления пользователями необходимо использовать какую-либо политику. Если допустимое свойство, связанное с политикой, является пустым, значит, для управления рассматриваемым пользователем используется глобальная политика, т. е. политика, которая автоматически применяется к пользователю, если ему не назначена специальная индивидуальная политика. Управление пользователями, которым не назначена политика клиента, осуществляется с помощью глобальной политики. Определить глобальную политику клиента поможет приведенная ниже команда.</span><span class="sxs-lookup"><span data-stu-id="73f5f-p107">With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="73f5f-151">См. также</span><span class="sxs-lookup"><span data-stu-id="73f5f-151">See also</span></span>

#### 

[<span data-ttu-id="73f5f-152">Управление Skype для бизнеса Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="73f5f-152">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="73f5f-153">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="73f5f-153">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="73f5f-154">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="73f5f-154">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

