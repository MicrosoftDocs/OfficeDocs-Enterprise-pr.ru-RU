---
title: "Создание учетных записей пользователей с помощью PowerShell в Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: PowerShell, Ent_Office_Other, O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "Сведения о том, как с помощью PowerShell в Office 365 создавать учетные записи пользователей в Office 365:."
ms.openlocfilehash: 58c4f6b1d75bb8b77cbf6616b8036dd753ddc3f3
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="60533-103">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="60533-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="60533-104">**Сводка.** Узнайте, как создавать учетные записи пользователей в Office 365, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60533-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="60533-p101">С помощью PowerShell можно эффективно создавать учетные записи пользователей, особенно если нужно создать сразу несколько. Создавая учетные записи пользователей в PowerShell, обязательно указывать некоторые свойства. Другие свойства необязательны для создания учетной записи, но важны для других целей. Эти свойства описываются в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="60533-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="60533-109">**Имя свойства**</span><span class="sxs-lookup"><span data-stu-id="60533-109">**Property name**</span></span>|<span data-ttu-id="60533-110">**Обязательный?**</span><span class="sxs-lookup"><span data-stu-id="60533-110">**Required?**</span></span>|<span data-ttu-id="60533-111">**Описание**</span><span class="sxs-lookup"><span data-stu-id="60533-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="60533-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="60533-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="60533-113">Да</span><span class="sxs-lookup"><span data-stu-id="60533-113">Yes</span></span>  <br/> |<span data-ttu-id="60533-p102">Это отображаемое имя, которое используется в службах Office 365, например Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="60533-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="60533-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="60533-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="60533-117">Да</span><span class="sxs-lookup"><span data-stu-id="60533-117">Yes</span></span>  <br/> |<span data-ttu-id="60533-p103">Это имя учетной записи, которое используется для входа в службы Office 365, например CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="60533-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="60533-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="60533-120">**FirstName**</span></span> <br/> |<span data-ttu-id="60533-121">Нет</span><span class="sxs-lookup"><span data-stu-id="60533-121">No</span></span>  <br/> ||
|<span data-ttu-id="60533-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="60533-122">**LastName**</span></span> <br/> |<span data-ttu-id="60533-123">Нет</span><span class="sxs-lookup"><span data-stu-id="60533-123">No</span></span>  <br/> ||
|<span data-ttu-id="60533-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="60533-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="60533-125">Нет</span><span class="sxs-lookup"><span data-stu-id="60533-125">No</span></span>  <br/> |<span data-ttu-id="60533-p104">Это план лицензирования (также называемый планом Office 365 или SKU), согласно которому учетной записи пользователя назначается доступная лицензия. Лицензия определяет, какие службы Office 365 доступны учетной записи пользователя. Создавая учетную запись, пользователю не обязательно назначать лицензию, но она необходима для доступа к службам Office 365. Лицензию необходимо добавить в течение 30 дней после создания учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="60533-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="60533-p105">Просмотреть планы лицензирования (**AccountSkuId**) и доступные лицензии организации можно с помощью командлета **Get-MsolAccountSku**. Дополнительные сведения см. в статье [Просмотр лицензий и служб с помощью PowerShell в Office 365](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="60533-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span></span><br/> |
|<span data-ttu-id="60533-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="60533-132">**Password**</span></span> <br/> |<span data-ttu-id="60533-133">Нет</span><span class="sxs-lookup"><span data-stu-id="60533-133">No</span></span>  <br/> | <span data-ttu-id="60533-p106">Если не укажете пароль, учетной записи пользователя будет назначен случайный пароль. Он будет показан в результатах выполнения команды. Собственный пароль должен отвечать перечисленным ниже требованиям к сложности.</span><span class="sxs-lookup"><span data-stu-id="60533-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="60533-136">Требуется указать от 8 до 16 текстовых знаков ASCII.</span><span class="sxs-lookup"><span data-stu-id="60533-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="60533-137">Знаки должны быть любого из четырех типов: строчные буквы, прописные буквы, числа и символы.</span><span class="sxs-lookup"><span data-stu-id="60533-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="60533-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="60533-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="60533-139">Нет</span><span class="sxs-lookup"><span data-stu-id="60533-139">No</span></span>  <br/> |<span data-ttu-id="60533-p107">Это действительный код страны по стандарту ISO 3166-1 alpha-2 (например, US для США и FR для Франции). Важно указать это значение, так как некоторые службы Office 365 недоступны в определенных странах. Следовательно, если это значение не указано, то учетной записи пользователя не удастся назначить лицензию. Дополнительные сведения см. в статье [О лицензионных ограничениях](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="60533-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="60533-144">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="60533-144">Before you begin</span></span>

<span data-ttu-id="60533-p108">Для выполнения действий, описанных в этой статье, требуется подключение к PowerShell. Инструкции см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="60533-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="60533-147">Создание учетных записей пользователей с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="60533-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="60533-148">Чтобы создать одну учетную запись, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="60533-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="60533-149">Этот пример кода создает учетную запись для пользователя в США с именем Caleb Sills и назначает для него лицензию согласно плану лицензирования  `contoso:ENTERPRISEPACK` (Office 365 для предприятий E3).</span><span class="sxs-lookup"><span data-stu-id="60533-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="60533-150">Создание нескольких учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="60533-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="60533-p109">Создайте CSV-файл, который содержит обязательные сведения об учетных записях пользователей. Пример:</span><span class="sxs-lookup"><span data-stu-id="60533-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="60533-153">Имена столбцов и их порядок в первой строке CSV-файла произвольны, но остальные данные в файле должны соответствовать порядку названий столбцов. Используйте названия столбцов в качестве значений параметров в команде PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60533-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="60533-154">Используйте указанный ниже синтаксис.</span><span class="sxs-lookup"><span data-stu-id="60533-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="60533-155">Этот пример кода создает учетные записи пользователей на основе файла NewAccounts.csv (C:\My Documents\NewAccounts.csv) и записывает результаты в файл NewAccountResults.csv (C:\My Documents\NewAccountResults.csv).</span><span class="sxs-lookup"><span data-stu-id="60533-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="60533-p110">Результаты можно просмотреть в выходном файле. Мы не указывали пароли, поэтому в выходном файле отображаются случайные значения.</span><span class="sxs-lookup"><span data-stu-id="60533-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="60533-158">Создание учетных записей пользователей с помощью модуля Azure Active Directory PowerShell версии 2</span><span class="sxs-lookup"><span data-stu-id="60533-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="60533-p111">Чтобы использовать командлет **New-AzureADUser** из модуля Azure Active Directory версии 2 для PowerShell, необходимо подключиться к подписке. Инструкции см. в статье [Подключение к Office 365](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="60533-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="60533-161">После подключения используйте следующий синтаксис, чтобы создать учетную запись:</span><span class="sxs-lookup"><span data-stu-id="60533-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="60533-162">В этом примере создается учетная запись пользователя Caleb Sills из Соединенных Штатов:</span><span class="sxs-lookup"><span data-stu-id="60533-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="60533-163">См. также</span><span class="sxs-lookup"><span data-stu-id="60533-163">See also</span></span>

<span data-ttu-id="60533-164">Сведения об управлении пользователями с помощью PowerShell для Office 365 см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="60533-164">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="60533-165">Удаление и восстановление учетных записей пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="60533-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="60533-166">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="60533-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="60533-167">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="60533-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="60533-168">Использование PowerShell в Office 365 для удаления лицензий из учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="60533-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="60533-169">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="60533-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="60533-170">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="60533-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- <span data-ttu-id="60533-171">[Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv);</span><span class="sxs-lookup"><span data-stu-id="60533-171">[Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)</span></span>
    
- [<span data-ttu-id="60533-172">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="60533-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="60533-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="60533-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="60533-174">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="60533-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

