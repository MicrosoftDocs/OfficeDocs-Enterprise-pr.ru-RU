---
title: Отключение доступа к службам с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Отключение доступа к службам Office 365 для пользователей с помощью PowerShell в Office 365.
ms.openlocfilehash: eb6099ce5a41d0ea0d09aba0b737be00912ffbdc
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841576"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="a42b1-103">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a42b1-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="a42b1-104">Когда учетной записи Office 365 назначена лицензия в плане лицензирования, службы Office 365 предоставляются пользователю из этой лицензии.</span><span class="sxs-lookup"><span data-stu-id="a42b1-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="a42b1-105">Тем не менее, вы можете управлять службами Office 365, к которым у пользователя есть доступ.</span><span class="sxs-lookup"><span data-stu-id="a42b1-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="a42b1-106">Например, несмотря на то, что лицензия разрешает доступ к службе SharePoint Online, вы можете отключить доступ к ней.</span><span class="sxs-lookup"><span data-stu-id="a42b1-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="a42b1-107">С помощью PowerShell можно отключить доступ к любому числу служб для определенного плана лицензирования:</span><span class="sxs-lookup"><span data-stu-id="a42b1-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="a42b1-108">отдельная учетная запись;</span><span class="sxs-lookup"><span data-stu-id="a42b1-108">An individual account.</span></span>
- <span data-ttu-id="a42b1-109">группа учетных записей;</span><span class="sxs-lookup"><span data-stu-id="a42b1-109">A group of accounts.</span></span>
- <span data-ttu-id="a42b1-110">все учетные записи в организации.</span><span class="sxs-lookup"><span data-stu-id="a42b1-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="a42b1-111">Существуют зависимости служб Office 365, которые могут препятствовать отключению указанной службы, когда от нее зависят другие службы.</span><span class="sxs-lookup"><span data-stu-id="a42b1-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a42b1-112">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a42b1-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a42b1-113">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="a42b1-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="a42b1-114">Затем используйте эту команду для просмотра доступных планов лицензирования, известных также как Аккаунтскуидс:</span><span class="sxs-lookup"><span data-stu-id="a42b1-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="a42b1-115">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="a42b1-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="a42b1-116">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a42b1-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="a42b1-117">Дополнительные сведения см. [в статье Просмотр лицензий и служб с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a42b1-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="a42b1-118">Чтобы просмотреть результаты процедуры, описанные в этом разделе, в статье [Просмотр сведений о лицензиях и службах для учетной записи с помощью Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a42b1-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="a42b1-119">Кроме того, вы можете воспользоваться сценарием PowerShell, который автоматизирует выполнение процедур, описанных в этой статье.</span><span class="sxs-lookup"><span data-stu-id="a42b1-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="a42b1-120">В частности, скрипт позволяет просматривать и отключать службы в организации Office 365, в том числе Sway.</span><span class="sxs-lookup"><span data-stu-id="a42b1-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="a42b1-121">Дополнительные сведения см. в статье [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a42b1-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="a42b1-122">Отключение определенных служб Office 365 для определенных пользователей по определенному плану лицензирования</span><span class="sxs-lookup"><span data-stu-id="a42b1-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="a42b1-123">Чтобы отключить определенный набор служб Office 365 для пользователей по определенному плану лицензирования, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="a42b1-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="a42b1-124">Шаг 1: определение нежелательных служб в плане лицензирования с помощью следующего синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="a42b1-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="a42b1-125">В следующем примере создается объект **LicenseOptions** , который отключает службы Office и SharePoint Online в плане лицензирования под названием `litwareinc:ENTERPRISEPACK` (Office 365 корпоративный E3).</span><span class="sxs-lookup"><span data-stu-id="a42b1-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="a42b1-126">Шаг 2: используйте объект **LicenseOptions** из шага 1 для одного или нескольких пользователей.</span><span class="sxs-lookup"><span data-stu-id="a42b1-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="a42b1-127">Чтобы создать учетную запись, для которой отключены службы, используйте указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="a42b1-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="a42b1-128">В следующем примере создается новая учетная запись для (Allie bellew), которая назначает лицензию и отключает службы, описанные в шаге 1.</span><span class="sxs-lookup"><span data-stu-id="a42b1-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="a42b1-129">Более подробную информацию о создании учетных записей пользователей в Office 365 PowerShell можно узнать в статье [Создание учетных записей пользователей с помощью office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a42b1-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="a42b1-130">Чтобы отключить службы для существующего лицензированного пользователя, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="a42b1-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="a42b1-131">В этом примере показано, как отключить службы для пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="a42b1-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="a42b1-132">Чтобы отключить службы, описанные в шаге 1, для всех существующих лицензированных пользователей, укажите имя плана Office 365 из отображения командлета **Get-MsolAccountSku** (например, **litwareinc: ENTERPRISEPACK**), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="a42b1-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="a42b1-133">Если вы используете командлет **Get – MsolUser** без параметра _ALL_ , возвращаются только первые 500 учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="a42b1-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="a42b1-134">Чтобы отключить службы для группы существующих пользователей, воспользуйтесь одним из указанных ниже методов для идентификации пользователей.</span><span class="sxs-lookup"><span data-stu-id="a42b1-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="a42b1-135">**Способ 1. Фильтрация учетных записей на основе существующего атрибута учетной записи**</span><span class="sxs-lookup"><span data-stu-id="a42b1-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="a42b1-136">Для этого используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a42b1-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="a42b1-137">В следующем примере отключаются службы для пользователей в отделе продаж в США.</span><span class="sxs-lookup"><span data-stu-id="a42b1-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="a42b1-138">**Способ 2: использование списка определенных учетных записей**</span><span class="sxs-lookup"><span data-stu-id="a42b1-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="a42b1-139">Для этого выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="a42b1-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="a42b1-140">Создайте текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="a42b1-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="a42b1-141">В этом примере текстовый файл имеет значение C:\\мои документы\\Accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="a42b1-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="a42b1-142">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="a42b1-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="a42b1-143">Если вы хотите отключить доступ к службам для нескольких планов лицензирования, повторите указанные выше инструкции для каждого плана лицензирования, убедившись в том, что:</span><span class="sxs-lookup"><span data-stu-id="a42b1-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="a42b1-144">Учетным записям пользователей назначен план лицензирования.</span><span class="sxs-lookup"><span data-stu-id="a42b1-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="a42b1-145">Службы, которые необходимо отключить, доступны в плане лицензирования.</span><span class="sxs-lookup"><span data-stu-id="a42b1-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="a42b1-146">Чтобы отключить службы Office 365 для пользователей при назначении их плану лицензирования, ознакомьтесь со статьей [Отключение доступа к службам при назначении пользовательских лицензий](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="a42b1-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="a42b1-147">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="a42b1-147">See also</span></span>

[<span data-ttu-id="a42b1-148">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a42b1-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a42b1-149">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="a42b1-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a42b1-150">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a42b1-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
