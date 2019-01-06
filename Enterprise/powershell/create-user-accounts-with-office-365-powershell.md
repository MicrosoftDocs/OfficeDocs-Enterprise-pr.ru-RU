---
title: Создание учетных записей пользователей с помощью PowerShell в Office 365
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Сведения о том, как с помощью PowerShell в Office 365 создавать учетные записи пользователей в Office 365:.
ms.openlocfilehash: 902f44dd4fc42d8f29ce92748cbbf1ce03c6615b
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730314"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="50389-103">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="50389-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="50389-104">**Сводка.** Узнайте, как создавать учетные записи пользователей в Office 365, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50389-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="50389-p101">С помощью PowerShell в Office 365 можно эффективно создавать учетные записи пользователей, особенно если нужно создать сразу несколько. При создании учетных записей пользователей в PowerShell в Office 365 указываются определенные свойства. Одни из них обязательны, другие  нет. Все свойства важны. Они описаны в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="50389-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="50389-109">**Имя свойства**</span><span class="sxs-lookup"><span data-stu-id="50389-109">**Property name**</span></span>|<span data-ttu-id="50389-110">**Обязательный?**</span><span class="sxs-lookup"><span data-stu-id="50389-110">**Required?**</span></span>|<span data-ttu-id="50389-111">**Описание**</span><span class="sxs-lookup"><span data-stu-id="50389-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="50389-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="50389-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="50389-113">Да</span><span class="sxs-lookup"><span data-stu-id="50389-113">Yes</span></span>  <br/> |<span data-ttu-id="50389-p102">Это отображаемое имя, которое используется в службах Office 365:. Например, Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="50389-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="50389-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="50389-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="50389-117">Да</span><span class="sxs-lookup"><span data-stu-id="50389-117">Yes</span></span>  <br/> |<span data-ttu-id="50389-p103">Это имя учетной записи, которое используется для входа в службы Office 365:. Например, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="50389-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="50389-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="50389-120">**FirstName**</span></span> <br/> |<span data-ttu-id="50389-121">Нет</span><span class="sxs-lookup"><span data-stu-id="50389-121">No</span></span>  <br/> ||
|<span data-ttu-id="50389-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="50389-122">**LastName**</span></span> <br/> |<span data-ttu-id="50389-123">Нет</span><span class="sxs-lookup"><span data-stu-id="50389-123">No</span></span>  <br/> ||
|<span data-ttu-id="50389-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="50389-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="50389-125">Нет</span><span class="sxs-lookup"><span data-stu-id="50389-125">No</span></span>  <br/> |<span data-ttu-id="50389-p104">Это план лицензирования (также называемый планом Office 365 или SKU), согласно которому учетной записи пользователя назначается доступная лицензия. Лицензия определяет, какие службы Office 365 доступны учетной записи пользователя. Создавая учетную запись, пользователю не обязательно назначать лицензию, но она необходима для доступа к службам Office 365. Лицензию необходимо добавить в течение 30 дней после создания учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="50389-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="50389-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="50389-130">**Password**</span></span> <br/> |<span data-ttu-id="50389-131">Нет</span><span class="sxs-lookup"><span data-stu-id="50389-131">No</span></span>  <br/> | <span data-ttu-id="50389-p105">Если не задать пароль, для учетной записи пользователя назначается случайный пароль, отображающийся в результатах выполнения команды. Если вы решили задать пароль самостоятельно, он должен содержать от 8 до 16 текстовых знаков ASCII любых трех типов из указанных далее: строчные буквы, прописные буквы, числа и символы.</span><span class="sxs-lookup"><span data-stu-id="50389-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="50389-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="50389-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="50389-135">Нет</span><span class="sxs-lookup"><span data-stu-id="50389-135">No</span></span>  <br/> |<span data-ttu-id="50389-p106">Это действительный код страны по стандарту ISO 3166-1 alpha-2 (например, US для США и FR для Франции). Важно указать это значение, так как некоторые службы Office 365 недоступны в определенных странах. Следовательно, если это значение не указано, то учетной записи пользователя не удастся назначить лицензию. Дополнительные сведения см. в статье [О лицензионных ограничениях](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="50389-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="50389-140">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="50389-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="50389-141">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="50389-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="50389-142">После подключения используйте следующий синтаксис, чтобы создать учетную запись:</span><span class="sxs-lookup"><span data-stu-id="50389-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="50389-143">В этом примере создается учетная запись пользователя Caleb Sills из Соединенных Штатов:</span><span class="sxs-lookup"><span data-stu-id="50389-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="50389-144">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="50389-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="50389-145">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="50389-145">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="50389-146">Создание одной учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="50389-146">Create an individual user account</span></span>

<span data-ttu-id="50389-147">Чтобы создать одну учетную запись, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="50389-147">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

<span data-ttu-id="50389-148">Чтобы предоставить список доступных имен плана лицензирования, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="50389-148">To list the available licensing plan names, use this command:</span></span>

````
Get-MsolAccountSku
````

<span data-ttu-id="50389-149">Этот пример кода создает учетную запись для пользователя в США с именем Caleb Sills и назначает для него лицензию согласно плану лицензирования `contoso:ENTERPRISEPACK` (Office 365 корпоративный E3).</span><span class="sxs-lookup"><span data-stu-id="50389-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="50389-150">Создание нескольких учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="50389-150">Create multiple user accounts</span></span>

1. <span data-ttu-id="50389-p107">Создайте CSV-файл, который содержит обязательные сведения об учетных записях пользователей. Пример:</span><span class="sxs-lookup"><span data-stu-id="50389-p107">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="50389-153">Имена столбцов и их порядок в первой строке CSV-файла произвольны, но остальные данные в файле должны соответствовать порядку названий столбцов. Используйте названия столбцов в качестве значений параметров в команде PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="50389-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="50389-154">Используйте указанный ниже синтаксис.</span><span class="sxs-lookup"><span data-stu-id="50389-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="50389-155">Этот пример кода создает учетные записи пользователей на основе файла NewAccounts.csv (C:\My Documents\NewAccounts.csv) и записывает результаты в файл NewAccountResults.csv (C:\My Documents\NewAccountResults.csv).</span><span class="sxs-lookup"><span data-stu-id="50389-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="50389-p108">Результаты можно просмотреть в выходном файле. Мы не указывали пароли, поэтому в выходном файле отображаются случайные значения, созданные Office 365.</span><span class="sxs-lookup"><span data-stu-id="50389-p108">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="50389-158">См. также</span><span class="sxs-lookup"><span data-stu-id="50389-158">See also</span></span>

[<span data-ttu-id="50389-159">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="50389-159">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="50389-160">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="50389-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="50389-161">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="50389-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
