---
title: Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.
ms.openlocfilehash: ce8e8c26e929132a8d4beb0f71e18c127064acbe
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="16602-103">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="16602-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="16602-104">**Сводка:**  В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.</span><span class="sxs-lookup"><span data-stu-id="16602-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="16602-p101">Лицензирование учетных записей пользователей в Office 365 важна, так как пользователи не могут использовать какие-либо службы Office 365, пока не лицензированных своей учетной записи. Office 365 PowerShell можно использовать для эффективного назначения лицензий нелицензированных учетным записям, особенно нескольких учетных записей.</span><span class="sxs-lookup"><span data-stu-id="16602-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="16602-107">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="16602-107">Before you begin</span></span>
<span data-ttu-id="16602-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="16602-108"></span></span>

- <span data-ttu-id="16602-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="16602-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="16602-p103">Командлет **Get-MsolAccountSku** используется для просмотра доступных планы лицензирования и число доступных лицензий в каждом плане в вашей организации. Число доступных лицензий в каждом плане — **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="16602-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="16602-114">Чтобы найти нелицензированных учетные записи в вашей организации, выполните команду`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="16602-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="16602-p104">Лицензии можно назначить только учетные записи пользователей, которые имеют свойство **UsageLocation** , равное допустимый код страны альфа-2 3166-1 ISO. Например, "мне НРАВИТСЯ" для США и FR для Франции. Некоторые службы Office 365 не доступны в некоторых странах. Для получения дополнительных сведений см [об ограничениях лицензии](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="16602-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="16602-p105">Чтобы найти учетные записи, которые не имеют значений **UsageLocation** , выполните команду `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Чтобы задать значение **UsageLocation** учетную запись, используйте следующий синтаксис `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Например `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="16602-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="16602-122">При использовании командлета **Get-MsolUser** без использования `-All` для параметра возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="16602-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="16602-123">Краткая версия (инструкции без пояснений)</span><span class="sxs-lookup"><span data-stu-id="16602-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="16602-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="16602-124"></span></span>

<span data-ttu-id="16602-p106">В этом разделе представлены процедуры без подробное объяснение. Если есть вопросы или для получения дополнительных сведений можно прочитать остальной части раздела.</span><span class="sxs-lookup"><span data-stu-id="16602-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="16602-127">Чтобы назначить лицензии пользователя, используйте следующий синтаксис в Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="16602-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="16602-128">В этом примере показывается назначение лицензии из `litwareinc:ENTERPRISEPACK` план лицензирования (Office 365 для предприятий E3) нелицензированных пользователю `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="16602-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="16602-129">Чтобы назначить лицензию большому количеству пользователей, используйте в следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="16602-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="16602-130">2^31 (****2 миллиардов терминов)</span><span class="sxs-lookup"><span data-stu-id="16602-130">**Notes**</span></span>
  
- <span data-ttu-id="16602-131">Невозможно назначить пользователю несколько лицензий из одного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="16602-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="16602-132">Если у вас нет достаточного количества доступных лицензий, назначаются лицензии для пользователей в том порядке, в случае возвращаемых командлетом **Get-MsolUser** , пока не истечет доступных лицензий.</span><span class="sxs-lookup"><span data-stu-id="16602-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="16602-133">В этом примере показывается назначение лицензии из `litwareinc:ENTERPRISEPACK` план лицензирования (Office 365 для предприятий E3) для всех пользователей без лицензий.</span><span class="sxs-lookup"><span data-stu-id="16602-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="16602-134">В этом примере назначаются те же лицензии пользователям без лицензий из отдела продаж в США.</span><span class="sxs-lookup"><span data-stu-id="16602-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="16602-135">Подробная версия (инструкции с подробными пояснениями)</span><span class="sxs-lookup"><span data-stu-id="16602-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="16602-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="16602-136"></span></span>

<span data-ttu-id="16602-p107">Как было указано в статье [Просмотр лицензионной и нелицензированных пользователей с Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), существует возможность для пользователей, имеющих допустимые учетные записи пользователей Office 365, но кто не было выдано лицензии Office 365. Это означает, что учетной записи или нет учетной записи, эти пользователи не смогут войти в Office 365. А если не может войти, невозможно использовать какие-либо службы Office 365.</span><span class="sxs-lookup"><span data-stu-id="16602-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="16602-140">В упомянутой выше статье также сказано, что можно вернуть список учетных записей нелицензированных пользователей с помощью команды:</span><span class="sxs-lookup"><span data-stu-id="16602-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="16602-141">Эта команда возвращает информацию обо всех пользователях, у которых сейчас нет лицензии на Office 365:</span><span class="sxs-lookup"><span data-stu-id="16602-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="16602-p108">Как вы видите, у нас есть один нелицензированных пользователей: Светлане Коноваловой. Так как мы перейдите о назначении Светлане лицензии Office 365?</span><span class="sxs-lookup"><span data-stu-id="16602-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="16602-144">Во-первых мы собираемся выполните командлет **Get-MsolAccountSku** , описанные в статье [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span><span class="sxs-lookup"><span data-stu-id="16602-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="16602-145">Эта команда возвращает данные, аналогичные приведенным ниже.</span><span class="sxs-lookup"><span data-stu-id="16602-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="16602-p109">Почему мы запустить **Get-MsolAccountSku** ? («Конфигурация» в случае, если вам интересно, — сокращение «единицы складского учета.» В нашем случае, — это просто бизнес-произнесите несколько слов для «продукт».) Существует две причины, почему мы выполнили **Get-MsolAccountSku**. Во-первых нужно убедитесь, что у нас есть лицензии для назначения Светлане. Мы у никаких лицензий, которые можно назначить ему? Чтобы определить, что мы вступили в значение свойства **ActiveUnits** (25) и вычитание значения свойства **WarningUnits** (0) и **ConsumedUnits** (24):</span><span class="sxs-lookup"><span data-stu-id="16602-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="16602-p110">Свойство **ActiveUnits** сообщает нам требуемое количество лицензий, мы приобретения и комбинацией **WarningUnits** и **ConsumedUnits** сообщает нам требуемое количество лицензий в настоящий момент используется. Если мы вычесть числа лицензий, уже голосовые для из числа лицензий, которые мы увидим, мы знаем, требуемое количество лицензий, по-прежнему доступны. Как удачи должен использовать ее, у нас есть одна лицензия для рассылки:</span><span class="sxs-lookup"><span data-stu-id="16602-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="16602-p111">Во-вторых, чтобы назначить новую лицензию необходимо знать имя нашей план лицензирования Светлане (то есть, мы должны знать **AccountSkuId** ). В этом случае очень просто: есть только один план лицензирования ( `litwareinc:ENTERPRISEPACK`). Обратите внимание, что может иметь несколько планы лицензирования в организации. В этом случае **Get-MsolAccountSku** вернет два разных **AccountSkuIds**, и вам потребуется выбрать подходящий план лицензирования при назначении лицензии. В данный момент тем не менее, мы будем пользуйтесь простом случае и Предположим, что у нас есть только один план лицензирования.</span><span class="sxs-lookup"><span data-stu-id="16602-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="16602-p112">*Затем так как назначить Светлане Коноваловой новую лицензию?* Типа того:</span><span class="sxs-lookup"><span data-stu-id="16602-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="16602-162">Это также вам нужно сделать: просто вызовите командлет **Set-MsolUserLicense** , убедившись, что задан параметр _UserPrincipalName_ для пользователя и соответствующего плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="16602-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="16602-163">**Set-MsolUserLicense** завершении запущена, вы увидите, что-то похожее на этот на экране:</span><span class="sxs-lookup"><span data-stu-id="16602-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\windows\system32>`
  
<span data-ttu-id="16602-p113">Другими словами он не будет похож на что-либо выполнена. Чтобы убедиться, что пользователю назначена лицензия, выполните команду следующим образом:</span><span class="sxs-lookup"><span data-stu-id="16602-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="16602-166">Если все сработало, вы увидите, что для свойства isLicensed Светланы теперь имеет значение True:</span><span class="sxs-lookup"><span data-stu-id="16602-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! Примечание по безопасности]<span data-ttu-id="16602-p114"> хороший вопрос: что делать, если ошибки и попытка присвоить лицензии пользователь, который уже имеет лицензии? Приведет к давая две лицензии для одного пользователя? > Быстрый ответ? Нет; Office 365 не позволяет назначить несколько лицензий с одним пользователем. (, Несколько лицензий из того же план лицензирования, который является.) При попытке выполнить, команда завершится с ошибкой с следующее сообщение об ошибке: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> признать, это сообщение об ошибке немного заблуждение: лицензия не будет действительно недопустимый, он просто назначается пользователю пользователей, которые уже *имеет* лицензии. Но, сообщение об ошибке, важно помнить, что один пользователь не получают несколько лицензий.</span><span class="sxs-lookup"><span data-stu-id="16602-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="16602-p115">Как вы только что видно, это очень простой в использовании Office 365 PowerShell назначение отдельная лицензия на одного пользователя. И, которая приводит к следующим изменениям очевидны вопрос: было бы просто, может быть еще проще назначить одну лицензию для одного пользователя с помощью центра администрирования Office 365? Ну, может; который зависит от, частично ли вы удобнее с помощью Windows PowerShell или удобнее с помощью центра администрирования Office 365. Где действительно ярко проявляются Windows PowerShell, однако при им необходимо назначить несколько лицензий для нескольких пользователей. Например эта команда назначает лицензии Office 365 для всех пользователей, которые еще не были установлены лицензии:</span><span class="sxs-lookup"><span data-stu-id="16602-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="16602-p116">В предыдущей команде используются **Такую** и параметр _UnlicensedUsersOnly_ для возврата коллекции всех учетных записей нелицензированных пользователей. Затем мы передаем этой коллекции в командлет **Set-MsolUserLicense** ; в свою очередь, **Set-MsolUserLicense** назначает лицензии (взяты из `litwareinc:ENTERPRISEPACK` план лицензирования) для каждого пользователя в коллекции.</span><span class="sxs-lookup"><span data-stu-id="16602-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="16602-p117">AH, но что делать, если у вас есть 5 нелицензированных пользователей, но только один доступные лицензии? В этом случае **Set-MsolUserLicense** предоставит доступные лицензии для первого пользователя, возвращенного **Get-MsolUser**. **Set-MsolUserLicense** принимающий попытается назначить лицензию четыре другим пользователям, но все четыре из этих попыток завершится ошибкой, а также следующее сообщение об ошибке:</span><span class="sxs-lookup"><span data-stu-id="16602-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="16602-p118">Другими словами Set-MsolUserLicense не будут давать сбой. Вместо этого он будет назначить любое количество лицензий, его можно. Только после этого он завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="16602-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="16602-p119">Давайте попробуйте другой пример. Возможно, вам нужно выполнить назначении лицензии для всех пользователей в отделе продаж. Ничего:</span><span class="sxs-lookup"><span data-stu-id="16602-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="16602-189">Чтобы выполнить задачу посложнее и свести к минимуму сообщения об ошибках и компьютерную обработку, просто назначьте лицензию нелицензированным пользователям из отдела продаж.</span><span class="sxs-lookup"><span data-stu-id="16602-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="16602-p120">В конце концов нет смысла попытке лицензии пользователям, которые уже имеют лицензию. Как мы уже видели, который не будут работать.</span><span class="sxs-lookup"><span data-stu-id="16602-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="16602-p121">Еще один пример. Возможно, вам нужно выполнить лицензии все пользователи США, у которых нет в настоящее время лицензии Office 365. В этом случае:</span><span class="sxs-lookup"><span data-stu-id="16602-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="16602-195">И так далее.</span><span class="sxs-lookup"><span data-stu-id="16602-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="16602-p122">Сколько времени для выполнения команды, скажем, выдает лицензии все нелицензированных пользователей? Это трудно сказать: зависит от числа пользователей, необходимо выполнить скорость подключения к сети. Если у вас есть несколько сотен пользователям пройдет достаточно быстро лицензии (то есть, его не следует занять более чем за минуту или две). Если у вас есть 10 000 пользователей, чтобы лицензировать его очевидно, что займет немного больше времени. Но не такая при условии, что потребуется для назначения лицензий на 10 000 пользователей с помощью центра администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="16602-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="16602-p123">До тех пор, пока мы по этой теме, здесь — это что-то необходимо уделить особое внимание при назначении лицензии: Если пользователь не имеет значения, настроенные для свойства **UsageLocation** не сможет назначить этому пользователю лицензии Office 365. Вместо этого вы получите сообщение об ошибке следующего вида:</span><span class="sxs-lookup"><span data-stu-id="16602-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="16602-p124">Таким образом, несколько roundabout это сообщение об ошибке сообщает нам о том, что пользователь не присвоен **UsageLocation**. Как можно было бы подумать, свойство **UsageLocation** (которая означает региона или страны, где пользователь обычно используется Office 365) очень важно. Почему? Так как службы, доступные пользователю зависит не только от пакета лицензирования, но также приобрести на котором находится пользователь: из-за локальных правил и правилам, некоторые службы могут быть недоступны для некоторых пользователей. Если пользователь не имеет **UsageLocation**, Office 365 не имеет возможности узнать, какие службы юридическую может быть доступно этому пользователю. Таким образом, Office 365 предоставление какие-либо службы для этого пользователя, по крайней мере не пока не были указаны **UsageLocation** .</span><span class="sxs-lookup"><span data-stu-id="16602-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="16602-p125">При настройке учетной записи пользователя вы узнаете сразу же если имеется каких-либо ограничений лицензии, связанные с указанной части мира. Например, если изменить **UsageLocation** для лицензированных пользователей в Иране ( `IR`), команда завершится с ошибкой с данное сообщение об ошибке: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> потому, что Office 365 не доступен для пользователей в Иране. Для получения дополнительных сведений см [об ограничениях лицензии](https://go.microsoft.com/fwlink/p/?LinkId=691730). Заметим страны двухбуквенный код, создаваемый международной организацией по стандартизации (ISO) используются Office 365. Эти коды можно найти на [веб-сайте ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span><span class="sxs-lookup"><span data-stu-id="16602-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="16602-214">Если вы хотите убедиться, что данный пользователь имеет **UsageLocation** , можно использовать команду, аналогичную этой:</span><span class="sxs-lookup"><span data-stu-id="16602-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="16602-215">Кроме того можно вернуть список всех пользователей, у которых нет **UsageLocation** с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="16602-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="16602-p126">При назначении лицензии пользователя этого пользователя будет по умолчанию предоставлен доступ ко всем службам Office 365, для которых есть доступ к вашей организации. К примеру Если вы приобрели лицензии для Office 365 для предприятий E3, недавно лицензированных пользователей будет автоматически предоставлен доступ к службам Exchange Online, Скайп для бизнеса в Интернет и SharePoint Online. Если вы хотите ограничить доступ пользователей к этим службам (например, может потребоваться пользователям иметь доступ к SharePoint Online, но *не* в Exchange Online и Скайп для бизнеса в Интернет) выберите в статье [отключить доступ к службам Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="16602-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="16602-219">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="16602-219">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="16602-220">Понятия</span><span class="sxs-lookup"><span data-stu-id="16602-220">See Also</span></span>
<span data-ttu-id="16602-221"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="16602-221"></span></span>

<span data-ttu-id="16602-222">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="16602-222">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="16602-223">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="16602-223">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="16602-224">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="16602-224">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="16602-225">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="16602-225">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="16602-226">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="16602-226">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="16602-227">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="16602-227">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="16602-228">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="16602-228">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="16602-229">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="16602-229">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="16602-230">SET-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="16602-230">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="16602-231">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="16602-231">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="16602-232">SELECT-Object</span><span class="sxs-lookup"><span data-stu-id="16602-232">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="16602-233">Where-Object</span><span class="sxs-lookup"><span data-stu-id="16602-233">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

