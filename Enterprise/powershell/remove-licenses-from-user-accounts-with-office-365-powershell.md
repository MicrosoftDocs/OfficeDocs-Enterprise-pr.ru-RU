---
title: Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям.
ms.openlocfilehash: a993737f4bd1186a7fb5beb7fa0f6a2ae6782618
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123306"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="3f28f-103">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="3f28f-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="3f28f-104">**Сводка:** Объясняет, как использовать Office 365 PowerShell для удаления лицензии Office 365, которые ранее были назначены пользователям.</span><span class="sxs-lookup"><span data-stu-id="3f28f-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="3f28f-105">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="3f28f-105">Before you begin</span></span>

- <span data-ttu-id="3f28f-p101">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="3f28f-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="3f28f-108">Чтобы просмотреть сведения о лицензировании плана (**AccountSkuID** ) в организации, в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="3f28f-108">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="3f28f-109">Просмотр лицензий и служб с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f28f-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="3f28f-110">Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="3f28f-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="3f28f-111">Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="3f28f-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="3f28f-112">Удаление лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="3f28f-112">Removing licenses from user accounts</span></span>

<span data-ttu-id="3f28f-113">Чтобы удалить лицензии из учетной записи пользователя, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="3f28f-113">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="3f28f-114">В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) с BelindaN@litwareinc.com учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="3f28f-114">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="3f28f-115">Чтобы удалить лицензии из группы лицензированных пользователей, используйте один из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="3f28f-115">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="3f28f-116">**Фильтрация учетных записей, на основе существующего атрибута учетной записи** Чтобы сделать это, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="3f28f-116">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="3f28f-117">В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) от всех accounts для сотрудников отдела продаж в США.</span><span class="sxs-lookup"><span data-stu-id="3f28f-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="3f28f-118">**Использование списка определенных учетных записей** Для этого выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="3f28f-118">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="3f28f-119">Создайте и сохраните текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="3f28f-119">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="3f28f-120">Используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="3f28f-120">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="3f28f-121">В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензии (Office 365 для предприятий E3) из учетных записей пользователей, определенных в текстовый файл C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="3f28f-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="3f28f-122">Чтобы удалить лицензии из всех учетных записей пользователей, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="3f28f-122">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="3f28f-123">В этом примере удаляется `litwareinc:ENTERPRISEPACK` лицензий (Office 365 для предприятий E3) для всех существующих учетных записей пользователей с корпоративным лицензированием.</span><span class="sxs-lookup"><span data-stu-id="3f28f-123">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="3f28f-p102">Другой способ освободить лицензия — путем удаления учетной записи пользователя. Для получения дополнительных сведений см [удаления и восстановления учетных записей пользователей с Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="3f28f-p102">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3f28f-126">См. также</span><span class="sxs-lookup"><span data-stu-id="3f28f-126">See also</span></span>

<span data-ttu-id="3f28f-127">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="3f28f-127">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="3f28f-128">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="3f28f-128">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3f28f-129">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="3f28f-129">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3f28f-130">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="3f28f-130">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3f28f-131">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="3f28f-131">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="3f28f-132">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="3f28f-132">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="3f28f-133">Get-Content</span><span class="sxs-lookup"><span data-stu-id="3f28f-133">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="3f28f-134">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="3f28f-134">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="3f28f-135">SET-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="3f28f-135">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="3f28f-136">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="3f28f-136">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="3f28f-137">Where-Object</span><span class="sxs-lookup"><span data-stu-id="3f28f-137">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="3f28f-138">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="3f28f-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

