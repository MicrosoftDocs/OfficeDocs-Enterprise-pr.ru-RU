---
title: Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
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
description: Объясняет, как использовать Office 365 PowerShell для определения служб Office 365, которые были назначены пользователям.
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213956"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="fc90e-103">Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fc90e-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="fc90e-104">**Сводка:** Объясняет, как использовать Office 365 PowerShell для определения служб Office 365, которые были назначены пользователям.</span><span class="sxs-lookup"><span data-stu-id="fc90e-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="fc90e-p101">В Office 365, лицензируемые из планы лицензирования (также называемое номера SKU или Office 365 планы) предоставить пользователям доступ к службам Office 365, определенных для этих планов. Тем не менее пользователь может отсутствовать доступ ко всем службам, которые доступны в лицензию, назначенных им. Office 365 PowerShell можно использовать для просмотра состояния службы на учетные записи пользователей.</span><span class="sxs-lookup"><span data-stu-id="fc90e-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="fc90e-108">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="fc90e-108">Before you begin</span></span>

- <span data-ttu-id="fc90e-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fc90e-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="fc90e-111">Используйте команды `Get-MsolAccountSku` и `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` для поиска со следующими сведениями:</span><span class="sxs-lookup"><span data-stu-id="fc90e-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="fc90e-112">Планы лицензирования, доступные в организации.</span><span class="sxs-lookup"><span data-stu-id="fc90e-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="fc90e-113">Службы, доступные в каждом плане лицензирования, и порядок, в котором они располагаются (индекс).</span><span class="sxs-lookup"><span data-stu-id="fc90e-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="fc90e-114">Дополнительные сведения о лицензировании планы, лицензии и службы можно [Просмотр лицензий и службы с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fc90e-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="fc90e-115">Используйте команду `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` поиск лицензий, назначенных пользователю, и порядок, в котором они являются из списка (индекс).</span><span class="sxs-lookup"><span data-stu-id="fc90e-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="fc90e-116">Если использовать командлет **Get-MsolUser** без параметра _All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="fc90e-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="fc90e-117">Чтобы просмотреть службы для учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="fc90e-117">To view services for a user account</span></span>

<span data-ttu-id="fc90e-118">Чтобы просмотреть все, которые пользователь имеет доступ к службам Office 365, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="fc90e-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="fc90e-p103">В этом примере показано служб, с которыми пользователь BelindaN@litwareinc.com имеет доступ. Это показывает службы, которые связаны с всех лицензий, которые были им назначены своей учетной записи.</span><span class="sxs-lookup"><span data-stu-id="fc90e-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="fc90e-121">Этот код показывает службы, к которым у пользователя BelindaN@litwareinc.com есть доступ по первой назначенной ей лицензии (индекс 0).</span><span class="sxs-lookup"><span data-stu-id="fc90e-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="fc90e-122">Чтобы просмотреть все службы для пользователя, которому назначена *несколько лицензий*, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="fc90e-122">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a><span data-ttu-id="fc90e-123">См. также</span><span class="sxs-lookup"><span data-stu-id="fc90e-123">See also</span></span>

<span data-ttu-id="fc90e-124">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="fc90e-124">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="fc90e-125">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fc90e-125">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc90e-126">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fc90e-126">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc90e-127">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fc90e-127">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc90e-128">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fc90e-128">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc90e-129">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="fc90e-129">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="fc90e-130">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="fc90e-130">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="fc90e-131">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="fc90e-131">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="fc90e-132">Format-List</span><span class="sxs-lookup"><span data-stu-id="fc90e-132">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="fc90e-133">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="fc90e-133">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="fc90e-134">SELECT-Object</span><span class="sxs-lookup"><span data-stu-id="fc90e-134">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="fc90e-135">Where-Object</span><span class="sxs-lookup"><span data-stu-id="fc90e-135">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="fc90e-136">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="fc90e-136">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]