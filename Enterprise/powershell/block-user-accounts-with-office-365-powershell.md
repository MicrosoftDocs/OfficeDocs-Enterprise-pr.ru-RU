---
title: Блокировка учетных записей пользователей с помощью PowerShell в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: 09cfdaf1485837713d03949cca456b9d07b66b00
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257670"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="2f04b-103">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="2f04b-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="2f04b-104">**Сводка:**  Сведения об использовании PowerShell в Office 365 для блокировки и разблокировки доступа к учетным записям Office 365.</span><span class="sxs-lookup"><span data-stu-id="2f04b-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="2f04b-105">Блокировка доступа к учетной записи Office 365 позволяет всем пользователям использовать эту учетную запись для входа и доступа к службам и данным в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="2f04b-105">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="2f04b-106">Вы можете использовать Office 365 PowerShell, чтобы заблокировать доступ к отдельным и нескольким учетным записям пользователей.</span><span class="sxs-lookup"><span data-stu-id="2f04b-106">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="2f04b-107">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="2f04b-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="2f04b-108">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="2f04b-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="2f04b-109">Блокировка доступа к отдельным учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="2f04b-109">Block access to individual user accounts</span></span>

<span data-ttu-id="2f04b-110">Используйте следующий синтаксис, чтобы заблокировать отдельную учетную запись пользователя:</span><span class="sxs-lookup"><span data-stu-id="2f04b-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="2f04b-111">Параметр – ObjectID в командлете Set – AzureAD принимает либо имя входа учетной записи, также называемое именем участника пользователя, либо идентификатор объекта учетной записи.</span><span class="sxs-lookup"><span data-stu-id="2f04b-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="2f04b-112">В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="2f04b-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="2f04b-113">Чтобы разблокировать эту учетную запись пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f04b-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="2f04b-114">Чтобы отобразить учетную запись участника-пользователя на основе отображаемого имени пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="2f04b-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="2f04b-115">В этом примере отображается имя участника-пользователя для учетной записи пользователя с именем Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="2f04b-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="2f04b-116">Чтобы заблокировать учетную запись на основе отображаемого имени пользователя, используйте следующие команды:</span><span class="sxs-lookup"><span data-stu-id="2f04b-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="2f04b-117">В любое время вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="2f04b-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="2f04b-118">Блокировка доступа к нескольким учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="2f04b-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="2f04b-119">Чтобы заблокировать доступ к нескольким учетным записям пользователей, создайте текстовый файл с одним именем входа учетной записи в каждой строке, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="2f04b-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="2f04b-120">В приведенных ниже командах приведен пример текстового файла "\ мои Documents\Accounts.txt.".</span><span class="sxs-lookup"><span data-stu-id="2f04b-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="2f04b-121">Замените путь и имя файла для текстового файла.</span><span class="sxs-lookup"><span data-stu-id="2f04b-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="2f04b-122">Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f04b-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="2f04b-123">Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f04b-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="2f04b-124">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f04b-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="2f04b-125">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2f04b-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="2f04b-126">Блокировка доступа к отдельным учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="2f04b-126">Block access to individual user accounts</span></span>

<span data-ttu-id="2f04b-127">Используйте следующий синтаксис, чтобы заблокировать доступ к отдельной учетной записи пользователя:</span><span class="sxs-lookup"><span data-stu-id="2f04b-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="2f04b-128">PowerShell Core не поддерживает модуль Microsoft Azure Active Directory для модуля Windows PowerShell и командлеты с **MSOL** в имени.</span><span class="sxs-lookup"><span data-stu-id="2f04b-128">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="2f04b-129">Чтобы продолжить использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f04b-129">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="2f04b-130">В этом примере блокируется доступ к учетной записи пользователя fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="2f04b-130">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="2f04b-131">Чтобы разблокировать учетную запись пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f04b-131">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="2f04b-132">В любое время вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="2f04b-132">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="2f04b-133">Блокировка доступа к нескольким учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="2f04b-133">Block access to multiple user accounts</span></span>

<span data-ttu-id="2f04b-134">Сначала создайте текстовый файл, который содержит одну учетную запись в каждой строке, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="2f04b-134">First, create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="2f04b-135">В приведенных ниже командах приведен пример текстового файла "\ мои Documents\Accounts.txt.".</span><span class="sxs-lookup"><span data-stu-id="2f04b-135">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="2f04b-136">Замените путь и имя файла для текстового файла.</span><span class="sxs-lookup"><span data-stu-id="2f04b-136">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="2f04b-137">Чтобы заблокировать доступ к учетным записям, перечисленным в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f04b-137">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="2f04b-138">Чтобы разблокировать учетные записи, перечисленные в текстовом файле, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2f04b-138">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="2f04b-139">См. также</span><span class="sxs-lookup"><span data-stu-id="2f04b-139">See also</span></span>

[<span data-ttu-id="2f04b-140">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f04b-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="2f04b-141">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="2f04b-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2f04b-142">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f04b-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
