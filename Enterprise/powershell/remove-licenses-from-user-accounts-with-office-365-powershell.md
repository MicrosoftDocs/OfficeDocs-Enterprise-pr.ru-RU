---
title: "Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей"
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
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям."
ms.openlocfilehash: c02d5a6cac029ce9beb8077da98418734d935ded
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="10057-103">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="10057-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="10057-104">**Сводка:** Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям.</span><span class="sxs-lookup"><span data-stu-id="10057-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="10057-105">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="10057-105">Before you begin</span></span>

- <span data-ttu-id="10057-p101">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="10057-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="10057-108">Чтобы просмотреть сведения о лицензировании плана ( **AccountSkuID** ) в организации, в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="10057-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - <span data-ttu-id="10057-109">[Просмотр лицензий и служб с помощью PowerShell в Office 365](view-licenses-and-services-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="10057-109">[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)</span></span>
    
  - <span data-ttu-id="10057-110">[Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="10057-110">[View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)</span></span>
    
- <span data-ttu-id="10057-111">Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="10057-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="10057-112">Краткая версия (инструкции без пояснений)</span><span class="sxs-lookup"><span data-stu-id="10057-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="10057-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="10057-113"></span></span>

<span data-ttu-id="10057-p102">В этом разделе процедуры представлены без лишних слов и объяснений. Если у вас возникнут вопросы или вам потребуются дополнительные сведения, вы можете прочитать остальные разделы статьи.</span><span class="sxs-lookup"><span data-stu-id="10057-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="10057-116">Чтобы удалить лицензии из учетной записи пользователя, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="10057-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="10057-117">В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) с BelindaN@litwareinc.com учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="10057-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="10057-118">Чтобы удалить лицензии из группы лицензированных пользователей, используйте один из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="10057-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="10057-119">**Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="10057-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="10057-120">В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) от всех accounts для сотрудников отдела продаж в США.</span><span class="sxs-lookup"><span data-stu-id="10057-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="10057-121">**Использование списка определенных учетных записей** Для этого выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="10057-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="10057-122">Создайте и сохраните текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="10057-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="10057-123">Используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="10057-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="10057-124">В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) из учетных записей пользователей, определенных в текстовый файл C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="10057-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="10057-125">Чтобы удалить лицензии из всех учетных записей пользователей, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="10057-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="10057-126">В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензий (Office 365 для предприятий E3) для всех существующих учетных записей пользователей с корпоративным лицензированием.</span><span class="sxs-lookup"><span data-stu-id="10057-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="10057-127">Подробная версия (инструкции с подробными пояснениями)</span><span class="sxs-lookup"><span data-stu-id="10057-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="10057-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="10057-128"></span></span>

<span data-ttu-id="10057-p103">Ничего не продолжается на непрерывно и, которая включает в себя лицензий на Office 365: быстрее или более поздних версий, поступит время, когда следует удалить лицензии из учетной записи пользователя. Возможно, вам будет пользователя на выходе; Возможно, вам больше не требуются лицензии; может быть -, существует очевидно, что любое количество причин, почему может потребоваться удаление пользовательской лицензии.</span><span class="sxs-lookup"><span data-stu-id="10057-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="10057-p104">Прежде чем продолжать любые дополнительные важно Обратите внимание на то, что удаление лицензия требуется для также, удалить лицензии: отключение всех служб на лицензия не то же самое удаление лицензии. Например предположим, что мы использовали копирование наших лицензии Office 365; Другими словами, мы имеет нет доступных никакой лицензии. Вы решили выполните процедуру в разделе [запрещать доступ к службам с помощью Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) , чтобы отключить все службы, скажем, Светлане Коноваловой для учетной записи. После этом, что количество лицензий будет у нас есть доступных? Верно: нулю. Да, процедуры из этого раздела будет *Отключить* всех служб на лицензия, но он не будет отключен (то есть, удаление) сама лицензия. Лицензии все еще будут действовать, и он будет по-прежнему будет назначенную. Она просто не сможет эта лицензия для получения доступа к какие-либо службы Office 365.</span><span class="sxs-lookup"><span data-stu-id="10057-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="10057-p105">И это важно: Если вы хотите удалить лицензии у пользователя должно фактически *Удалить* лицензии. Отключение всех служб будет мешают пользователю подключиться Office 365, но он не будет Освободите место на свой лицензии. Если вы хотите получить обратно лицензию, назначенную пользователю, вам нужно выполнить команду, подставив свои значения, команда, которая использует параметр _RemoveLicenses_ для непосредственного удаления лицензии, ранее назначенную Светлане:</span><span class="sxs-lookup"><span data-stu-id="10057-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="10057-142">Выполнения этой команды и Светлане Коноваловой больше не будет лицензии на использование Office 365.</span><span class="sxs-lookup"><span data-stu-id="10057-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="10057-p106">Как вы видите, если используется параметр _RemoveLicenses_ , необходимо указать имя лицензии, который требуется удалить. Если вы не знаете, какой план лицензирования использовалась при назначении лицензии пользователя, просто выполните команду следующего вида:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="10057-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="10057-145">Чтобы убедиться, что лицензия удалена, выполните такую команду, чтобы проверить интересующую учетную запись пользователя:</span><span class="sxs-lookup"><span data-stu-id="10057-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="10057-146">Если все выполнено согласно плану, для свойства **isLicensed** Светланы теперь должно быть задано `False`:</span><span class="sxs-lookup"><span data-stu-id="10057-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="10057-p107">Другой способ освободить лицензия — путем удаления учетной записи пользователя. Для получения дополнительных сведений см [удаления и восстановления учетных записей пользователей с Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="10057-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="10057-149">См. также</span><span class="sxs-lookup"><span data-stu-id="10057-149">See also</span></span>

<span data-ttu-id="10057-150">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="10057-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="10057-151">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="10057-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="10057-152">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="10057-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="10057-153">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="10057-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="10057-154">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="10057-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="10057-155">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="10057-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="10057-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="10057-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="10057-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="10057-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="10057-158">SET-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="10057-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="10057-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="10057-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="10057-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="10057-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="10057-161">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="10057-161">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

