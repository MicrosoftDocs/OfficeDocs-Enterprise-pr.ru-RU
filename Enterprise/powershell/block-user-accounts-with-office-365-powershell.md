---
title: "Блокировка учетных записей пользователей с помощью PowerShell в Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Описание способов блокировать и разблокировать доступ к учетным записям Office 365 с помощью Office 365 PowerShell."
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="fb8eb-103">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fb8eb-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="fb8eb-104">**Сводка:**  Описание способов блокировать и разблокировать доступ к учетным записям Office 365 с помощью Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="fb8eb-p101">Блокирование доступа к учетной записи Office 365 не позволяет другим пользователям с помощью учетной записи для входа и доступ к службам и данных в организации Office 365. При блокировании доступа к учетной записи, пользователь получает сообщение об ошибке при попытке входа в:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. When you block access to the account, the user receives the following error message when they attempt to sign in:</span></span>
  
![Заблокированная учетная запись Office 365.](images/o365_powershell_account_blocked.png)
  
<span data-ttu-id="fb8eb-108">Office 365 PowerShell можно использовать для блокировки доступа к отдельным и несколько учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-108">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="fb8eb-109">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="fb8eb-109">Before you begin</span></span>

- <span data-ttu-id="fb8eb-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fb8eb-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="fb8eb-112">При блокировании учетной записи пользователя, может потребоваться в течение 24 часов вступили в силу на устройствах пользователей и клиентов.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-112">When you block a user account, it might take as long as 24 hours to take effect on all the user's devices and clients.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="fb8eb-113">Блокировка доступа к отдельным учетным записям пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fb8eb-113">Use Office 365 PowerShell to block access to individual user accounts</span></span>

<span data-ttu-id="fb8eb-114">Используйте следующий синтаксис, чтобы заблокировать доступ к отдельной учетной записи пользователя:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-114">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

<span data-ttu-id="fb8eb-115">В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-115">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="fb8eb-116">Чтобы разблокировать учетную запись пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-116">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

<span data-ttu-id="fb8eb-117">В любое время можно проверить заблокированных состояние учетной записи пользователя, с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a><span data-ttu-id="fb8eb-118">Заблокируйте доступ к нескольким учетным записям пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb8eb-118">Use Office 365 PowerShell to block access to multiple user accounts</span></span>

<span data-ttu-id="fb8eb-119">Во-первых создайте текстовый файл, содержащий одну учетную запись в каждой строке следующим образом:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-119">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="fb8eb-p103">В следующие команды в текстовом файле пример — C:\My Documents\Accounts.txt. Замените путь и имя текстового файла.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="fb8eb-122">Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="fb8eb-123">Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a><span data-ttu-id="fb8eb-124">Блокировка доступа к учетным записям пользователей с помощью модуля Azure Active Directory PowerShell 2</span><span class="sxs-lookup"><span data-stu-id="fb8eb-124">Use the Azure Active Directory V2 PowerShell module to block access to user accounts</span></span>

<span data-ttu-id="fb8eb-p104">Чтобы использовать командлет **New-AzureADUser** из модуля Azure Active Directory PowerShell 2, сначала необходимо подключиться к подписке. Инструкции см. в разделе[Подключение с помощью модуля Azure Active Directory PowerShell 2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="fb8eb-p104">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="fb8eb-127">После этого используйте следующий синтаксис, чтобы заблокировать отдельную учетную запись пользователя:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-127">After you have connected, use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="fb8eb-128">Параметр -ObjectID в командлете Set-AzureAD принимает либо имя учетной записи (имя участника-пользователя), либо идентификатор объекта учетной записи.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-128">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="fb8eb-129">В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="fb8eb-130">Чтобы разблокировать эту учетную запись пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-130">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="fb8eb-131">Для отображения имени участника-пользователя на основании отображаемое имя пользователя учетной записи пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-131">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="fb8eb-132">В этом примере отображается учетной записи пользователя имени участника-пользователя для пользователя с именем Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-132">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fb8eb-133">Чтобы заблокировать учетную запись на основе имени пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-133">To block an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="fb8eb-134">В любое время можно проверить заблокированных состояние учетной записи пользователя, с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-134">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

<span data-ttu-id="fb8eb-135">Чтобы заблокировать доступ к нескольким учетным записям пользователей, создайте текстовый файл, содержащий одно имя учетной записи в каждой строке следующим образом:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-135">To block access to multiple user accounts, create a text file that contains one account name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="fb8eb-p105">В следующие команды в текстовом файле пример — C:\My Documents\Accounts.txt. Замените путь и имя текстового файла.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-p105">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="fb8eb-138">Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-138">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="fb8eb-139">Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-139">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a><span data-ttu-id="fb8eb-140">См. также</span><span class="sxs-lookup"><span data-stu-id="fb8eb-140">See also</span></span>
<span data-ttu-id="fb8eb-141"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="fb8eb-141"></span></span>

<span data-ttu-id="fb8eb-142">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="fb8eb-142">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="fb8eb-143">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fb8eb-143">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fb8eb-144">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fb8eb-144">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fb8eb-145">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="fb8eb-145">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fb8eb-146">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="fb8eb-146">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="fb8eb-147">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="fb8eb-147">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="fb8eb-148">Get-Content</span><span class="sxs-lookup"><span data-stu-id="fb8eb-148">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [<span data-ttu-id="fb8eb-149">SET-MsolUser</span><span class="sxs-lookup"><span data-stu-id="fb8eb-149">Set-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [<span data-ttu-id="fb8eb-150">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="fb8eb-150">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

