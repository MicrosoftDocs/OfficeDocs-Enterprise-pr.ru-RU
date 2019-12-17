---
title: Блокировка учетных записей пользователей с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Сведения об использовании PowerShell в Office 365 для блокировки и разблокировки доступа к учетным записям Office 365.
ms.openlocfilehash: 2ebed63de7cddd536b42000028cabd3c71cec31b
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072251"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="88b8e-103">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="88b8e-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="88b8e-104">Блокировка доступа к учетной записи Office 365 позволяет всем пользователям использовать эту учетную запись для входа и доступа к службам и данным в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="88b8e-104">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="88b8e-105">Вы можете использовать Office 365 PowerShell, чтобы заблокировать доступ к отдельным и нескольким учетным записям пользователей.</span><span class="sxs-lookup"><span data-stu-id="88b8e-105">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="88b8e-106">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="88b8e-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="88b8e-107">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="88b8e-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="88b8e-108">Блокировка доступа к отдельным учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="88b8e-108">Block access to individual user accounts</span></span>

<span data-ttu-id="88b8e-109">Используйте следующий синтаксис, чтобы заблокировать отдельную учетную запись пользователя:</span><span class="sxs-lookup"><span data-stu-id="88b8e-109">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="88b8e-110">Параметр – ObjectID в командлете Set – AzureAD принимает либо имя входа учетной записи, также называемое именем участника пользователя, либо идентификатор объекта учетной записи.</span><span class="sxs-lookup"><span data-stu-id="88b8e-110">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="88b8e-111">В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="88b8e-111">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="88b8e-112">Чтобы разблокировать эту учетную запись пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="88b8e-112">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="88b8e-113">Чтобы отобразить учетную запись участника-пользователя на основе отображаемого имени пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="88b8e-113">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="88b8e-114">В этом примере отображается имя участника-пользователя для учетной записи пользователя с именем Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="88b8e-114">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="88b8e-115">Чтобы заблокировать учетную запись на основе отображаемого имени пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="88b8e-115">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="88b8e-116">В любое время вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="88b8e-116">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="88b8e-117">Блокировка доступа к нескольким учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="88b8e-117">Block access to multiple user accounts</span></span>

<span data-ttu-id="88b8e-118">Чтобы заблокировать доступ к нескольким учетным записям пользователей, создайте текстовый файл с одним именем входа учетной записи в каждой строке, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="88b8e-118">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="88b8e-119">В приведенных ниже командах приведен пример текстового файла "\ мои Documents\Accounts.txt.".</span><span class="sxs-lookup"><span data-stu-id="88b8e-119">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="88b8e-120">Замените путь и имя файла для текстового файла.</span><span class="sxs-lookup"><span data-stu-id="88b8e-120">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="88b8e-121">Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="88b8e-121">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="88b8e-122">Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="88b8e-122">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="88b8e-123">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="88b8e-123">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="88b8e-124">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="88b8e-124">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="88b8e-125">Блокировка доступа к отдельным учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="88b8e-125">Block access to individual user accounts</span></span>

<span data-ttu-id="88b8e-126">Используйте следующий синтаксис, чтобы заблокировать доступ к отдельной учетной записи пользователя:</span><span class="sxs-lookup"><span data-stu-id="88b8e-126">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="88b8e-127">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="88b8e-127">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="88b8e-128">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88b8e-128">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="88b8e-129">В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="88b8e-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="88b8e-130">Чтобы разблокировать учетную запись пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="88b8e-130">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="88b8e-131">В любое время вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="88b8e-131">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="88b8e-132">Блокировка доступа к нескольким учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="88b8e-132">Block access to multiple user accounts</span></span>

<span data-ttu-id="88b8e-133">Сначала создайте текстовый файл, который содержит одну учетную запись в каждой строке, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="88b8e-133">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="88b8e-134">В приведенных ниже командах приведен пример текстового файла "\ мои Documents\Accounts.txt.".</span><span class="sxs-lookup"><span data-stu-id="88b8e-134">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="88b8e-135">Замените путь и имя файла для текстового файла.</span><span class="sxs-lookup"><span data-stu-id="88b8e-135">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="88b8e-136">Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="88b8e-136">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="88b8e-137">Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="88b8e-137">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="88b8e-138">См. также</span><span class="sxs-lookup"><span data-stu-id="88b8e-138">See also</span></span>

[<span data-ttu-id="88b8e-139">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="88b8e-139">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="88b8e-140">Управление Office 365 с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="88b8e-140">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="88b8e-141">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="88b8e-141">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
