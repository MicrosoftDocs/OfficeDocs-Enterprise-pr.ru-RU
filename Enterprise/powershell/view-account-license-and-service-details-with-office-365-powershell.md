---
title: "Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: "Объясняет, как использовать Office 365 PowerShell для определения служб Office 365, которые были назначены пользователям."
ms.openlocfilehash: 69784b43e6e2b24f776d07a937877e5ae0c74888
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="790f1-103">Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="790f1-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="790f1-104">**Сводка:** Объясняет, как использовать Office 365 PowerShell для определения служб Office 365, которые были назначены пользователям.</span><span class="sxs-lookup"><span data-stu-id="790f1-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="790f1-p101">В Office 365, лицензируемые из планы лицензирования (также называемое номера SKU или Office 365 планы) предоставить пользователям доступ к службам Office 365, определенных для этих планов. Тем не менее пользователь может отсутствовать доступ ко всем службам, которые доступны в лицензию, назначенных им. Office 365 PowerShell можно использовать для просмотра состояния службы на учетные записи пользователей.</span><span class="sxs-lookup"><span data-stu-id="790f1-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="790f1-108">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="790f1-108">Before you begin</span></span>
<span data-ttu-id="790f1-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="790f1-109"></span></span>

- <span data-ttu-id="790f1-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="790f1-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="790f1-112">Используйте команды `Get-MsolAccountSku` и `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` для поиска со следующими сведениями:</span><span class="sxs-lookup"><span data-stu-id="790f1-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="790f1-113">Планы лицензирования, доступные в организации.</span><span class="sxs-lookup"><span data-stu-id="790f1-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="790f1-114">Службы, доступные в каждом плане лицензирования, и порядок, в котором они располагаются (индекс).</span><span class="sxs-lookup"><span data-stu-id="790f1-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="790f1-115">Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="790f1-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="790f1-116">Используйте команду `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` поиск лицензий, назначенных пользователю, и порядок, в котором они являются из списка (индекс).</span><span class="sxs-lookup"><span data-stu-id="790f1-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="790f1-117">Если использовать командлет **Get-MsolUser** без параметра _All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="790f1-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="790f1-118">Краткая версия (инструкции без пояснений)</span><span class="sxs-lookup"><span data-stu-id="790f1-118">The short version (instructions without explanations)</span></span>
<span data-ttu-id="790f1-119"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="790f1-119"></span></span>

<span data-ttu-id="790f1-120">Для просмотра всех служб Office 365 PowerShell, которые пользователь имеет доступ к, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="790f1-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="790f1-p103">В этом примере показано служб, с которыми пользователь BelindaN@litwareinc.com имеет доступ. Это показывает службы, которые связаны с всех лицензий, которые были им назначены своей учетной записи.</span><span class="sxs-lookup"><span data-stu-id="790f1-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="790f1-123">Этот код показывает службы, к которым у пользователя BelindaN@litwareinc.com есть доступ по первой назначенной ей лицензии (индекс 0).</span><span class="sxs-lookup"><span data-stu-id="790f1-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="790f1-124">Чтобы найти всех лицензированных пользователей, для которых включены или отключены определенные службы, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="790f1-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="790f1-125">В этих примерах используются следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="790f1-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="790f1-126">Лицензии, который предоставляет доступ к службам Office 365, которые мы будем рады — это первый лицензии, назначенной для всех пользователей (номер индекса 0).</span><span class="sxs-lookup"><span data-stu-id="790f1-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="790f1-p104">Службы Office 365, которые мы будем рады, Скайп для бизнеса в Интернет и Exchange Online. Для лицензий, которые связаны с план лицензирования, Скайп для бизнеса в Интернет — 6-й служба, из списка (номер индекса — 5), и Exchange Online — 9 служба перечисленных (индекс равен 8).</span><span class="sxs-lookup"><span data-stu-id="790f1-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="790f1-129">В этом примере возвращаются все лицензированных пользователей, которым разрешена Скайп для бизнеса в Интернет и Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="790f1-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="790f1-130">В этом примере возвращаются всех лицензированных пользователей, не включенных в Скайп для бизнеса в Интернет или Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="790f1-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="790f1-131">Подробная версия (инструкции с подробными пояснениями)</span><span class="sxs-lookup"><span data-stu-id="790f1-131">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="790f1-132"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="790f1-132"></span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="790f1-133">Поиск служб Office 365 PowerShell, которые пользователь имеет доступ к</span><span class="sxs-lookup"><span data-stu-id="790f1-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="790f1-p105">Важно очевидно, что вам необходимо знать, какие пользователи выданных лицензий на Office 365 и пользователей, которые еще не. (В статье [Просмотр лицензионной и нелицензированных пользователей с Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) для получения дополнительных сведений). Тем не менее просто создавая лицензии Office 365 не сообщает, что-либо о что этого пользователя можно выполнять с помощью Office 365. Можно использовать пользователь Exchange Online или Скайп для бизнеса в Интернет? Можно этому пользователю доступ к SharePoint Online? Он или она имеет доступ к Office профессиональный плюс? Наличия лицензии означает, что пользователь может получить доступ к этим службам. Тем не менее возможности, доступные пользователю зависят от службы, которые будут включены в его лицензии.</span><span class="sxs-lookup"><span data-stu-id="790f1-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="790f1-p106">Так как же нам определять, который компонентов Office 365 пользователь имеет доступ к? Для этого необходимо выполнить команду, подставив свои значения:</span><span class="sxs-lookup"><span data-stu-id="790f1-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="790f1-144">В этой команде используется командлет **Get-MsolUser** возвращает сведения об учетной записи BelindaN@litwareinc.com. Мы возвращении эти сведения, мы передавать данные учетной записи в командлет **Select-Object** и попросите **Select-Object** «разверните» значение свойства **лицензии** :</span><span class="sxs-lookup"><span data-stu-id="790f1-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="790f1-p107">Зачем мы это делаем? Также по умолчанию **лицензий** свойство сообщает нам только имя пакета лицензирования, откуда лицензия:</span><span class="sxs-lookup"><span data-stu-id="790f1-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="790f1-147">«Разворачивание» свойства **Licenses** предоставляет нам немного больше информации:</span><span class="sxs-lookup"><span data-stu-id="790f1-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="790f1-148">И затем, развернув свойство **ServiceStatus** мы можем вернуть еще больше информации:</span><span class="sxs-lookup"><span data-stu-id="790f1-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="790f1-149">Служба плана \*\*\*</span><span class="sxs-lookup"><span data-stu-id="790f1-149">****Service plan****</span></span>|<span data-ttu-id="790f1-150">Описание \*\*\*</span><span class="sxs-lookup"><span data-stu-id="790f1-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="790f1-151">Sway</span><span class="sxs-lookup"><span data-stu-id="790f1-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="790f1-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="790f1-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="790f1-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="790f1-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="790f1-154">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="790f1-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="790f1-155">Office профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="790f1-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="790f1-156">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="790f1-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="790f1-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="790f1-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="790f1-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="790f1-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="790f1-159">Exchange Online (план 2)</span><span class="sxs-lookup"><span data-stu-id="790f1-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="790f1-p108">Вы сказать, что это слишком много кода? Также, если вы пугает маленьким запутанность Windows PowerShell, можно запустить эту сжатую версию команды вместо: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="790f1-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="790f1-p109">В случае, если вам интересно, мы может «разверните узел» свойства **Licenses** поскольку **лицензий** является свойством: это отдельное свойство, которое можно хранить несколько значений. Когда мы разверните значение свойства, которые мы просто детализировать получите эти дополнительные значения, которые по умолчанию не отображаются на экране.</span><span class="sxs-lookup"><span data-stu-id="790f1-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="790f1-p110">Так как вы должны знать, что значение является многозначным свойством? Чтобы выяснить это, запустите команду следующего вида: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> командлета **Get-member** , возвращает сведения об объекте. в этом случае сведения о свойстве значений, составляющих объект учетной записи пользователя. Вот что может сказать о свойства **Licenses** **Get-Member** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> при определении свойств что-либо говорится о коллекциях (в этом случае `System.Collections.Generic.List`) то вы знаете, вы имеете дело с многозначным свойством.</span><span class="sxs-lookup"><span data-stu-id="790f1-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="790f1-p111">Так что же это все значит? Чтобы ответить на этот вопрос, сперва новый взгляд на информацию, возвращенную командлетом **Get-MsolUser** :</span><span class="sxs-lookup"><span data-stu-id="790f1-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

<span data-ttu-id="790f1-169">И давайте также взглянем на таблицу, объясняется, что самом деле представляют эти планы обслуживания со странными именами:</span><span class="sxs-lookup"><span data-stu-id="790f1-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="790f1-170">Служба плана \*\*\*</span><span class="sxs-lookup"><span data-stu-id="790f1-170">****Service plan****</span></span>|<span data-ttu-id="790f1-171">Описание \*\*\*</span><span class="sxs-lookup"><span data-stu-id="790f1-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="790f1-172">Sway</span><span class="sxs-lookup"><span data-stu-id="790f1-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="790f1-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="790f1-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="790f1-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="790f1-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="790f1-175">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="790f1-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="790f1-176">Office профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="790f1-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="790f1-177">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="790f1-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="790f1-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="790f1-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="790f1-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="790f1-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="790f1-180">Exchange Online (план 2)</span><span class="sxs-lookup"><span data-stu-id="790f1-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="790f1-p112">Этих?  `MCOSTANDARD` — это просто внутренних программирования имен для Скайп для бизнеса в Интернет, а `OFFICESUSBCRIPTION` — это просто внутренних программирования имя для приложений Office профессиональный плюс. Это не самое интуитивно в мире, но до тех пор, пока в этой таблице держать под рукой не будут иметь множество проблем при работе со службами Office 365.</span><span class="sxs-lookup"><span data-stu-id="790f1-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="790f1-p113">Но подождите: больше. Как мы узнали в статье [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), если задано значение **ProvisioningStatus** `Success` , который означает, что служба полностью включен; Например если `MCOSTANDARD` задано значение `Success` , который означает, что пользователь может получить доступ к Скайп для бизнеса в Интернет. Если задано значение **ProvisioningStatus** `PendingInput` , который означает, что Office 365 все еще обрабатывает запрос службы; Тем не менее пользователь может обычно войдите в систему и доступа к службе во время завершения обработки запроса. ( `YAMMER_ENTERPRISE` всегда отображается как `PendingInput`, но это не важно:, который не остановит пользователя подключение к сети Yammer).</span><span class="sxs-lookup"><span data-stu-id="790f1-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="790f1-188">Пользователи могут устанавливать и активировать новую установку Office профессиональный плюс при `OFFICESUBSCRIPTION` в `PendingInput` состояние.</span><span class="sxs-lookup"><span data-stu-id="790f1-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="790f1-189">И нет необходимости говорить, — это служба задано значение `Disabled` , который означает, что соответствующая служба недоступна для пользователя.</span><span class="sxs-lookup"><span data-stu-id="790f1-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="790f1-190">Поиск пользователей, имеющих доступ к определенным службам Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="790f1-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="790f1-p114">В отдельных статьях было показано, как использовать Office 365 PowerShell для отключения доступа пользователей к службам. (Если вы пропустили этой статье, см. [Отключение доступа к службам с помощью Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Которая приводит к следующим изменениям очевидны вопрос: какой вид, чтобы определить, какие *Пользователи* (то есть несколько пользователей) имеют служб включен или отключен?</span><span class="sxs-lookup"><span data-stu-id="790f1-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="790f1-p115">Мы надежде, что кто-то задаст. Чтобы ответить на этот вопрос, давайте рассмотрим таблицы службы, которые мы сначала рассмотрены в статье [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) для нашего доступны только план лицензирования `litwareinc:ENTERPRISEPACK`:</span><span class="sxs-lookup"><span data-stu-id="790f1-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="790f1-196">Служба плана \*\*\*</span><span class="sxs-lookup"><span data-stu-id="790f1-196">****Service plan****</span></span>|<span data-ttu-id="790f1-197">Описание \*\*\*</span><span class="sxs-lookup"><span data-stu-id="790f1-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="790f1-198">Sway</span><span class="sxs-lookup"><span data-stu-id="790f1-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="790f1-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="790f1-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="790f1-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="790f1-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="790f1-201">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="790f1-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="790f1-202">Office профессиональный плюс</span><span class="sxs-lookup"><span data-stu-id="790f1-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="790f1-203">Skype для бизнеса Online</span><span class="sxs-lookup"><span data-stu-id="790f1-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="790f1-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="790f1-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="790f1-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="790f1-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="790f1-206">Exchange Online (план 2)</span><span class="sxs-lookup"><span data-stu-id="790f1-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="790f1-p116">Как вы помните, план обслуживания не больше, чем внутреннее имя программирования для продукта; например `OFFICESUBSCRIPTION`, имени одно, — это внутреннее имя программирования в Office профессиональный плюс. Если `OFFICESUBSCRIPTION` отображается как `SUCCESS` на план обслуживания пользователя, затем это означает, что пользователь может получить доступ к Office профессиональный плюс. Если `EXCHANGE_S_ENTERPRISE` указана в качестве `DISABLED` , который означает, что пользователь не может использовать Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="790f1-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="790f1-210">Пользователи могут устанавливать и активировать новую установку Office профессиональный плюс при `OFFICESUBSCRIPTION` в `PendingInput` состояние.</span><span class="sxs-lookup"><span data-stu-id="790f1-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="790f1-p117">Необходимо на данном этапе где порядок служб играет важнейшую роль. Windows PowerShell присваивает индекс для каждой записи в списке. Первой записи равно 0, следующей записи — 1 и т. д. В следующей таблице описаны результаты:</span><span class="sxs-lookup"><span data-stu-id="790f1-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="790f1-215">Номер индекса \*\*\*</span><span class="sxs-lookup"><span data-stu-id="790f1-215">****Index number****</span></span>|<span data-ttu-id="790f1-216">Служба плана \*\*\*</span><span class="sxs-lookup"><span data-stu-id="790f1-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="790f1-217">0</span><span class="sxs-lookup"><span data-stu-id="790f1-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="790f1-218">1</span><span class="sxs-lookup"><span data-stu-id="790f1-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="790f1-219">2</span><span class="sxs-lookup"><span data-stu-id="790f1-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="790f1-220">3</span><span class="sxs-lookup"><span data-stu-id="790f1-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="790f1-221">4</span><span class="sxs-lookup"><span data-stu-id="790f1-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="790f1-222">5</span><span class="sxs-lookup"><span data-stu-id="790f1-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="790f1-223">6</span><span class="sxs-lookup"><span data-stu-id="790f1-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="790f1-224">7</span><span class="sxs-lookup"><span data-stu-id="790f1-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="790f1-225">8</span><span class="sxs-lookup"><span data-stu-id="790f1-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="790f1-226">Как вы видите, `SWAY` первой службы в списке, поэтому он получает номер индекса 0.</span><span class="sxs-lookup"><span data-stu-id="790f1-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="790f1-p118">Почему 0, а не 1? Это связано с программирования очередь. В языки программирования индексы указано, как далеко элемент является «смещение» от начала массива. Первый элемент *является* начала массива, поэтому его смещение равно 0. Второй элемент является 1 элемент от начала массива, поэтому его смещение равно 1.</span><span class="sxs-lookup"><span data-stu-id="790f1-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="790f1-p119">Давайте попробуйте пример. Предположим, что мы хотели бы список всех лицензированных пользователей, которые не были активированы для Exchange Online. Для этого можно использовать следующую команду:</span><span class="sxs-lookup"><span data-stu-id="790f1-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="790f1-p120">Конечно это шифрованное нужна маленьким команды, давайте уйти около минуты объяснить, как это работает. Это фактически команда двух частей и первая часть очень просто: мы используем командлет **Get-MsolUser** возвращает коллекцию всех наших пользователей Office 365 (лицензированным и нелицензированных):</span><span class="sxs-lookup"><span data-stu-id="790f1-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="790f1-p121">Эти сведения затем передается в командлет **Where-Object** . **Where-Object** проходит через все учетные записи пользователей и выполняет поиск этих учетных записей, необходимых для обоих следующим критериям:</span><span class="sxs-lookup"><span data-stu-id="790f1-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="790f1-p122">Для свойства **isLicensed** равно ( `-eq`) `True` ( `$true`). Который позволяет исключить пользователей без лицензий.</span><span class="sxs-lookup"><span data-stu-id="790f1-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="790f1-p123">Значение лицензий **[0]. ServiceStatus [8]. ProvisioningStatus** свойство равно ( `-eq`) `Disabled`. В нашем интерпретации важной частью имя громоздкими свойства состоит в следующем.</span><span class="sxs-lookup"><span data-stu-id="790f1-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="790f1-p124">`[8]` Представляет номер индекса для Exchange Online. (Мы знаем, обратившись в таблице несколько минут назад). Что делать, если требуется найти всем пользователям, включенным для Скайп для бизнеса в Интернет? Также номер индекса для Скайп для бизнеса в Интернет — 5, мы используем следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="790f1-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="790f1-247">И так далее.</span><span class="sxs-lookup"><span data-stu-id="790f1-247">Etc., etc.</span></span>
    
    <span data-ttu-id="790f1-p125">Заметим `Licenses[0]` указывает, план лицензирования, который нужно просмотреть. Поскольку домена в нашей тестовой среде имеет только один план лицензирования это не имеет значения намного. Однако предположим, что у нас пользователя, которому назначена лицензии из двух разных планы лицензирования. В этом случае `Licenses[0]` представляет первый план лицензирования и `Licenses[1]` представляет второй план лицензирования.</span><span class="sxs-lookup"><span data-stu-id="790f1-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="790f1-252">Чтобы найти лицензии, назначенные пользователю, и порядок, в котором они располагаются, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="790f1-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="790f1-p126">Вы видите, как это работает? Номер индекса для приложений Office профессиональный плюс — 4; Таким образом эта команда возвращает список всех пользователей, которые не были активированы для приложений Office профессиональный плюс:</span><span class="sxs-lookup"><span data-stu-id="790f1-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="790f1-p127">А что делать, если мы хотели список пользователей, которые были *включены* в Office профессиональный плюс? Если вы был включен, вашей **ServiceStatus** будет `PendingInput` или `Success`; Другими словами, будет вашей **ServiceStatus** *не* равенства ( `-ne`) `Disabled`. Это означает, что все, нужно сделать — вступили в нашей предыдущей команды и заменить `-eq` оператор для `-ne` оператор:</span><span class="sxs-lookup"><span data-stu-id="790f1-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="790f1-p128">Как говорят переходит, что код, вероятно, не будут win много Конкурсы преимущество. И достоверность сказали, код может получить еще больше запутанную. Например предположим, что для просмотра для пользователей, которым разрешена для обеих Скайп для бизнеса в Интернет и Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="790f1-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="790f1-p129">Но не выполнения слишком много о как вас, который может иметь вид: важно, что с относительно небольшим минимальными усилиями, можно извлечь эти сведения. Не удается получить в эти же сведения, с помощью центра администрирования Office 365? Теоретически, Да, но, в практике, нет. Чтобы получить в эти же сведения, с помощью центра администрирования Office 365 необходимо просмотреть сведения о лицензировании для каждого пользователя, один пользователь за раз и затем вручную отслеживание пользователей, которые включены для *X* и пользователей, которые еще не. Который будет работать, но давайте честно: при наличии более чем 10 или 11 пользователей не понадобятся для этого. Это слишком утомительным и занимать много времени.</span><span class="sxs-lookup"><span data-stu-id="790f1-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="790f1-267">Конечно, являющийся зачем нам Windows PowerShell: Windows PowerShell позволяет сохранить вы утомительные и длительные задачи, например.</span><span class="sxs-lookup"><span data-stu-id="790f1-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="790f1-268">Хотя мы на него, здесь приведена ключевая команда для просмотра сведений о службе:</span><span class="sxs-lookup"><span data-stu-id="790f1-268">While we're at it, here's the ultimate command for viewing service information:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

<span data-ttu-id="790f1-p130">И это очень дурацких команды. Однако он создает CSV-файла, отображение всех пользователей и всего их состояние службы.</span><span class="sxs-lookup"><span data-stu-id="790f1-p130">And yes, that's a very crazy-looking command. But it creates a CSV file showing all of your users and all of their service statuses.</span></span>

  
## <a name="see-also"></a><span data-ttu-id="790f1-271">См. также</span><span class="sxs-lookup"><span data-stu-id="790f1-271">See also</span></span>
<span data-ttu-id="790f1-272"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="790f1-272"></span></span>

<span data-ttu-id="790f1-273">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="790f1-273">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="790f1-274">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="790f1-274">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="790f1-275">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="790f1-275">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="790f1-276">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="790f1-276">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="790f1-277">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="790f1-277">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="790f1-278">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="790f1-278">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="790f1-279">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="790f1-279">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="790f1-280">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="790f1-280">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="790f1-281">Format-List</span><span class="sxs-lookup"><span data-stu-id="790f1-281">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="790f1-282">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="790f1-282">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="790f1-283">SELECT-Object</span><span class="sxs-lookup"><span data-stu-id="790f1-283">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="790f1-284">Where-Object</span><span class="sxs-lookup"><span data-stu-id="790f1-284">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="790f1-285">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="790f1-285">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]