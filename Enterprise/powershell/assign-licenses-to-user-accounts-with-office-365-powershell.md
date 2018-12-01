---
title: Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
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
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123296"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="885ee-103">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="885ee-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="885ee-104">**Сводка:**  В данной статье описывается использование Office 365 PowerShell назначение лицензии Office 365 для нелицензированных пользователей.</span><span class="sxs-lookup"><span data-stu-id="885ee-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="885ee-p101">Лицензирование учетных записей пользователей в Office 365 важна, так как пользователи не могут использовать какие-либо службы Office 365, пока не лицензированных своей учетной записи. Office 365 PowerShell можно использовать для эффективного назначения лицензий нелицензированных учетным записям, особенно нескольких учетных записей.</span><span class="sxs-lookup"><span data-stu-id="885ee-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="885ee-107">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="885ee-107">Before you begin</span></span>
<span data-ttu-id="885ee-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="885ee-108"></span></span>

- <span data-ttu-id="885ee-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="885ee-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="885ee-p103">Командлет **Get-MsolAccountSku** используется для просмотра доступных планы лицензирования и число доступных лицензий в каждом плане в вашей организации. Число доступных лицензий в каждом плане — **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="885ee-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="885ee-114">Чтобы найти нелицензированных учетные записи в вашей организации, выполните команду`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="885ee-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="885ee-p104">Лицензии можно назначить только учетные записи пользователей, которые имеют свойство **UsageLocation** , равное допустимый код страны альфа-2 3166-1 ISO. Например, "мне НРАВИТСЯ" для США и FR для Франции. Некоторые службы Office 365 не доступны в некоторых странах. Для получения дополнительных сведений см [об ограничениях лицензии](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="885ee-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="885ee-p105">Чтобы найти учетные записи, которые не имеют значений **UsageLocation** , выполните команду `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Чтобы задать значение **UsageLocation** учетную запись, используйте следующий синтаксис `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Например `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="885ee-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="885ee-122">При использовании командлета **Get-MsolUser** без использования `-All` для параметра возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="885ee-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="885ee-123">Назначение лицензий для учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="885ee-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="885ee-124">Чтобы назначить лицензии пользователя, используйте следующий синтаксис в Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="885ee-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="885ee-125">В этом примере показывается назначение лицензии из `litwareinc:ENTERPRISEPACK` план лицензирования (Office 365 для предприятий E3) нелицензированных пользователю `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="885ee-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="885ee-126">Чтобы назначить лицензию большому количеству пользователей, используйте в следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="885ee-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="885ee-127">**Примечания**</span><span class="sxs-lookup"><span data-stu-id="885ee-127">**Notes**</span></span>
  
- <span data-ttu-id="885ee-128">Невозможно назначить пользователю несколько лицензий из одного плана лицензирования.</span><span class="sxs-lookup"><span data-stu-id="885ee-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="885ee-129">Если у вас нет достаточного количества доступных лицензий, они назначаются пользователям в порядке, в котором их возвращает командлет **Get-MsolUser**, пока не закончатся.</span><span class="sxs-lookup"><span data-stu-id="885ee-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="885ee-130">В этом примере показывается назначение лицензии из `litwareinc:ENTERPRISEPACK` план лицензирования (Office 365 для предприятий E3) для всех пользователей без лицензий.</span><span class="sxs-lookup"><span data-stu-id="885ee-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="885ee-131">В этом примере назначаются те же лицензии пользователям без лицензий из отдела продаж в США.</span><span class="sxs-lookup"><span data-stu-id="885ee-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="885ee-132">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="885ee-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="885ee-133">См. также</span><span class="sxs-lookup"><span data-stu-id="885ee-133">See also</span></span>
<span data-ttu-id="885ee-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="885ee-134"></span></span>

<span data-ttu-id="885ee-135">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="885ee-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="885ee-136">Создание учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="885ee-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="885ee-137">Удаление и восстановление учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="885ee-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="885ee-138">Блокировки учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="885ee-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="885ee-139">Удалить лицензии у учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="885ee-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="885ee-140">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="885ee-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="885ee-141">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="885ee-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="885ee-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="885ee-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="885ee-143">SET-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="885ee-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="885ee-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="885ee-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="885ee-145">SELECT-Object</span><span class="sxs-lookup"><span data-stu-id="885ee-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="885ee-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="885ee-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

