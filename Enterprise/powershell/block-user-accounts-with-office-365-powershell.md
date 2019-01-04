---
title: Блокировка учетных записей пользователей с помощью PowerShell в Office 365
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Описание способов блокировать и разблокировать доступ к учетным записям Office 365 с помощью Office 365 PowerShell.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546480"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="24516-103">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="24516-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="24516-104">**Сводка:**  Описание способов блокировать и разблокировать доступ к учетным записям Office 365 с помощью Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24516-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="24516-p101">Блокирование доступа к учетной записи Office 365 не позволяет другим пользователям с помощью учетной записи для входа и доступ к службам и данных в организации Office 365. Office 365 PowerShell можно использовать для блокировки доступа к отдельным и несколько учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="24516-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="24516-107">Использование Windows Azure Active Directory PowerShell для модуля "график"</span><span class="sxs-lookup"><span data-stu-id="24516-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="24516-108">Во-первых, [подключиться к клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="24516-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="24516-109">Заблокируйте доступ к учетным записям отдельных пользователей</span><span class="sxs-lookup"><span data-stu-id="24516-109">Block access to individual user accounts</span></span>

<span data-ttu-id="24516-110">Чтобы заблокировать отдельные учетные записи, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="24516-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="24516-111">Параметр - ObjectID в командлет Set-AzureAD принимает либо имя учетной записи входа, имя участника-пользователя или идентификатор учетной записи.</span><span class="sxs-lookup"><span data-stu-id="24516-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="24516-112">В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="24516-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="24516-113">Чтобы разблокировать эту учетную запись пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="24516-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="24516-114">Для отображения имени участника-пользователя на основании отображаемое имя пользователя учетной записи пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="24516-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="24516-115">В этом примере отображается учетной записи пользователя имени участника-пользователя для пользователя с именем Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="24516-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="24516-116">Чтобы заблокировать на основании отображаемое имя пользователя учетной записи, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="24516-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="24516-117">В любое время можно проверить заблокированных состояние учетной записи пользователя, с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="24516-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="24516-118">Заблокируйте доступ к нескольким учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="24516-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="24516-119">Чтобы заблокировать доступ к нескольким учетным записям пользователей, создайте текстовый файл, содержащий одну учетную запись учетное имя в каждой строке следующим образом:</span><span class="sxs-lookup"><span data-stu-id="24516-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="24516-p102">В следующие команды в текстовом файле пример — C:\My Documents\Accounts.txt. Замените путь и имя текстового файла.</span><span class="sxs-lookup"><span data-stu-id="24516-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="24516-122">Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="24516-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="24516-123">Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="24516-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="24516-124">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24516-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="24516-125">Во-первых, [подключиться к клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="24516-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="24516-126">Заблокируйте доступ к учетным записям отдельных пользователей</span><span class="sxs-lookup"><span data-stu-id="24516-126">Block access to individual user accounts</span></span>

<span data-ttu-id="24516-127">Используйте следующий синтаксис, чтобы заблокировать доступ к отдельной учетной записи пользователя:</span><span class="sxs-lookup"><span data-stu-id="24516-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="24516-128">В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="24516-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="24516-129">Чтобы разблокировать учетную запись пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="24516-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="24516-130">В любое время можно проверить заблокированных состояние учетной записи пользователя, с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="24516-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="24516-131">Заблокируйте доступ к нескольким учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="24516-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="24516-132">Во-первых создайте текстовый файл, содержащий одну учетную запись в каждой строке следующим образом:</span><span class="sxs-lookup"><span data-stu-id="24516-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="24516-p103">В следующие команды в текстовом файле пример — C:\My Documents\Accounts.txt. Замените путь и имя текстового файла.</span><span class="sxs-lookup"><span data-stu-id="24516-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="24516-135">Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="24516-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="24516-136">Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="24516-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="24516-137">См. также</span><span class="sxs-lookup"><span data-stu-id="24516-137">See also</span></span>

[<span data-ttu-id="24516-138">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="24516-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="24516-139">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="24516-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="24516-140">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="24516-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
