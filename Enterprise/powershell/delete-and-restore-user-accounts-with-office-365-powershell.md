---
title: Удаление учетных записей пользователей с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
description: Узнайте, как удалять учетные записи пользователей Office 365, используя PowerShell.
ms.openlocfilehash: 0b882f3bdf9070c83baffaca65a7c80c98cd4ed9
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546470"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="5609f-103">Удаление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="5609f-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="5609f-104">**Сводка.** Узнайте, как удалять учетные записи пользователей Office 365, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5609f-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="5609f-105">Чтобы удалить учетную запись пользователя, можно использовать PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="5609f-105">You can use Office 365 PowerShell to delete a user account.</span></span>

   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5609f-106">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="5609f-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5609f-107">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="5609f-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="5609f-108">После подключения используйте следующий синтаксис, чтобы удалить учетную запись пользователя:</span><span class="sxs-lookup"><span data-stu-id="5609f-108">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="5609f-109">В этом примере удаляется учетная запись пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="5609f-109">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="5609f-110">Параметр **-ObjectID** в командлете **Remove-AzureAD** принимает либо имя учетной записи, используемое для входа (имя участника-пользователя), либо идентификатор объекта учетной записи.</span><span class="sxs-lookup"><span data-stu-id="5609f-110">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="5609f-111">Чтобы отобразить имя учетной записи на основе имени пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="5609f-111">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5609f-112">В этом примере отображается имя учетной записи пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="5609f-112">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5609f-113">Чтобы удалить учетную запись на основе отображаемого имени пользователя, используйте указанные ниже команды:</span><span class="sxs-lookup"><span data-stu-id="5609f-113">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5609f-114">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5609f-114">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="5609f-p101">Учетную запись пользователя, удаленную с помощью модуля Microsoft Azure Active Directory для Windows PowerShell, можно восстановить в течение 30 дней.</span><span class="sxs-lookup"><span data-stu-id="5609f-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="5609f-117">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5609f-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="5609f-118">Чтобы удалить учетную запись пользователя, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="5609f-118">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="5609f-119">В этом примере удаляется учетная запись пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="5609f-119">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="5609f-120">Чтобы восстановить удаленную учетную запись пользователя в течение 30 дней, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="5609f-120">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="5609f-121">В этом примере восстанавливается удаленная учетная запись BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="5609f-121">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="5609f-122">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="5609f-122">**Notes:**</span></span>
  
- <span data-ttu-id="5609f-123">Чтобы просмотреть список удаленных пользователей, которых можно восстановить, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="5609f-123">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="5609f-124">Если исходное имя участника-пользователя используется другой учетной записью, замените _NewUserPrincipalName_ параметром _UserPrincipalName_, чтобы указать другое имя участника-пользователя при восстановлении учетной записи.</span><span class="sxs-lookup"><span data-stu-id="5609f-124">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="5609f-125">См. также</span><span class="sxs-lookup"><span data-stu-id="5609f-125">See also</span></span>

[<span data-ttu-id="5609f-126">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5609f-126">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5609f-127">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="5609f-127">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5609f-128">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5609f-128">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

