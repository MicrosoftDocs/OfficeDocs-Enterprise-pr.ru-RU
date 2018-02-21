---
title: "Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365"
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
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Узнайте, как удалять и восстанавливать учетные записи пользователей Office 365, используя PowerShell."
ms.openlocfilehash: 09f3595ed7cd5434efb2897a43ba1bbca5286c25
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c0b87-103">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="c0b87-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c0b87-104">**Сводка.** Узнайте, как удалять и восстанавливать учетные записи пользователей Office 365, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0b87-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="c0b87-p101">Учетную запись пользователя, удаленную с помощью PowerShell в Office 365, можно восстановить в течение 30 дней.</span><span class="sxs-lookup"><span data-stu-id="c0b87-p101">When you use Office 365 PowerShell to delete a user account, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="c0b87-107">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="c0b87-107">Before you begin</span></span>

- <span data-ttu-id="c0b87-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c0b87-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c0b87-110">Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="c0b87-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="c0b87-111">Блокировка доступа к отдельным учетным записям пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="c0b87-111">Use Office 365 PowerShell to block access to individual user accounts</span></span>
<span data-ttu-id="c0b87-112"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="c0b87-112"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="c0b87-113">Чтобы удалить учетную запись пользователя, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="c0b87-113">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="c0b87-114">В этом примере удаляется учетная запись пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="c0b87-114">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="c0b87-115">Чтобы восстановить удаленную учетную запись пользователя в течение 30 дней, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="c0b87-115">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="c0b87-116">В этом примере восстанавливается удаленная учетная запись BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="c0b87-116">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="c0b87-117">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="c0b87-117">**Notes:**</span></span>
  
- <span data-ttu-id="c0b87-118">Чтобы просмотреть список удаленных пользователей, которых можно восстановить, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c0b87-118">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="c0b87-119">Если исходное имя участника-пользователя используется другой учетной записью, замените  _NewUserPrincipalName_ параметром _UserPrincipalName_, чтобы указать другое имя участника-пользователя при восстановлении учетной записи.</span><span class="sxs-lookup"><span data-stu-id="c0b87-119">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a><span data-ttu-id="c0b87-120">Удаление учетной записи пользователя с помощью модуля Azure Active Directory PowerShell 2</span><span class="sxs-lookup"><span data-stu-id="c0b87-120">Use the Azure Active Directory V2 PowerShell module to remove a user account</span></span>
<span data-ttu-id="c0b87-121"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="c0b87-121"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="c0b87-p103">Чтобы использовать командлет **Remove-AzureADUser** из модуля Azure Active Directory 2 для PowerShell, сначала необходимо подключиться к подписке ([инструкции](https://go.microsoft.com/fwlink/?linkid=842218)).</span><span class="sxs-lookup"><span data-stu-id="c0b87-p103">To use the **Remove-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="c0b87-124">После подключения используйте следующий синтаксис, чтобы удалить учетную запись пользователя:</span><span class="sxs-lookup"><span data-stu-id="c0b87-124">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <Account>
```

<span data-ttu-id="c0b87-125">В этом примере удаляется учетная запись пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="c0b87-125">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="c0b87-126">Параметр **-ObjectID** в командлете **Remove-AzureAD** принимает либо имя учетной записи (имя участника-пользователя), либо идентификатор объекта учетной записи.</span><span class="sxs-lookup"><span data-stu-id="c0b87-126">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="c0b87-127">Чтобы отобразить имя учетной записи на основе имени пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="c0b87-127">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c0b87-128">В этом примере отображается имя учетной записи пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="c0b87-128">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c0b87-129">Чтобы удалить учетную запись на основе имени пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="c0b87-129">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a><span data-ttu-id="c0b87-130">См. также</span><span class="sxs-lookup"><span data-stu-id="c0b87-130">See also</span></span>
<span data-ttu-id="c0b87-131"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="c0b87-131"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="c0b87-132">Сведения об управлении пользователями с помощью PowerShell для Office 365 см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="c0b87-132">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="c0b87-133">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="c0b87-133">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c0b87-134">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="c0b87-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c0b87-135">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="c0b87-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c0b87-136">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="c0b87-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="c0b87-137">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="c0b87-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="c0b87-138">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c0b87-138">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="c0b87-139">Remove-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c0b87-139">Remove-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [<span data-ttu-id="c0b87-140">Restore-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c0b87-140">Restore-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [<span data-ttu-id="c0b87-141">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="c0b87-141">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

