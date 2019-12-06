---
title: Отключение доступа к службам с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/04/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Отключение доступа к службам Office 365 для пользователей с помощью PowerShell в Office 365.
ms.openlocfilehash: 9668175010b2581bcdd40988f605f68eea30520d
ms.sourcegitcommit: 572375d69c438bd1eae012e6e98039be0a126a6d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/06/2019
ms.locfileid: "39872247"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="ed56a-103">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed56a-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="ed56a-104">Когда учетной записи Office 365 назначена лицензия в плане лицензирования, службы Office 365 предоставляются пользователю из этой лицензии.</span><span class="sxs-lookup"><span data-stu-id="ed56a-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="ed56a-105">Тем не менее, вы можете управлять службами Office 365, к которым у пользователя есть доступ.</span><span class="sxs-lookup"><span data-stu-id="ed56a-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="ed56a-106">Например, несмотря на то, что лицензия разрешает доступ к службе SharePoint Online, вы можете отключить доступ к ней.</span><span class="sxs-lookup"><span data-stu-id="ed56a-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="ed56a-107">С помощью PowerShell можно отключить доступ к любому числу служб для определенного плана лицензирования:</span><span class="sxs-lookup"><span data-stu-id="ed56a-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="ed56a-108">отдельная учетная запись;</span><span class="sxs-lookup"><span data-stu-id="ed56a-108">An individual account.</span></span>
- <span data-ttu-id="ed56a-109">группа учетных записей;</span><span class="sxs-lookup"><span data-stu-id="ed56a-109">A group of accounts.</span></span>
- <span data-ttu-id="ed56a-110">все учетные записи в организации.</span><span class="sxs-lookup"><span data-stu-id="ed56a-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="ed56a-111">Существуют зависимости служб Office 365, которые могут препятствовать отключению указанной службы, когда от нее зависят другие службы.</span><span class="sxs-lookup"><span data-stu-id="ed56a-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ed56a-112">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed56a-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ed56a-113">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ed56a-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="ed56a-114">Затем используйте эту команду для просмотра доступных планов лицензирования, известных также как Аккаунтскуидс:</span><span class="sxs-lookup"><span data-stu-id="ed56a-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="ed56a-115">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="ed56a-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="ed56a-116">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed56a-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="ed56a-117">Дополнительные сведения см. [в статье Просмотр лицензий и служб с помощью Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ed56a-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="ed56a-118">Чтобы просмотреть результаты процедуры, описанные в этом разделе, в статье [Просмотр сведений о лицензиях и службах для учетной записи с помощью Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ed56a-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="ed56a-119">Кроме того, вы можете воспользоваться сценарием PowerShell, который автоматизирует выполнение процедур, описанных в этой статье.</span><span class="sxs-lookup"><span data-stu-id="ed56a-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="ed56a-120">В частности, скрипт позволяет просматривать и отключать службы в организации Office 365, в том числе Sway.</span><span class="sxs-lookup"><span data-stu-id="ed56a-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="ed56a-121">Дополнительные сведения см. в статье [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ed56a-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="ed56a-122">Отключение определенных служб Office 365 для определенных пользователей по определенному плану лицензирования</span><span class="sxs-lookup"><span data-stu-id="ed56a-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="ed56a-123">Чтобы отключить определенный набор служб Office 365 для пользователей по определенному плану лицензирования, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="ed56a-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="ed56a-124">Шаг 1: определение нежелательных служб в плане лицензирования с помощью следующего синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="ed56a-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="ed56a-125">В следующем примере создается объект **LicenseOptions** , который отключает службы Office и SharePoint Online в плане лицензирования под названием `litwareinc:ENTERPRISEPACK` (Office 365 корпоративный E3).</span><span class="sxs-lookup"><span data-stu-id="ed56a-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="ed56a-126">Шаг 2: используйте объект **LicenseOptions** из шага 1 для одного или нескольких пользователей.</span><span class="sxs-lookup"><span data-stu-id="ed56a-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="ed56a-127">Чтобы создать учетную запись, для которой отключены службы, используйте указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="ed56a-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="ed56a-128">В следующем примере создается новая учетная запись для (Allie bellew), которая назначает лицензию и отключает службы, описанные в шаге 1.</span><span class="sxs-lookup"><span data-stu-id="ed56a-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="ed56a-129">Более подробную информацию о создании учетных записей пользователей в Office 365 PowerShell можно узнать в статье [Создание учетных записей пользователей с помощью office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ed56a-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="ed56a-130">Чтобы отключить службы для существующего лицензированного пользователя, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="ed56a-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="ed56a-131">В этом примере показано, как отключить службы для пользователя BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="ed56a-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="ed56a-132">Чтобы отключить службы, описанные в шаге 1, для всех существующих лицензированных пользователей, укажите имя плана Office 365 из отображения командлета **Get-MsolAccountSku** (например, **litwareinc: ENTERPRISEPACK**), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="ed56a-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="ed56a-133">Если вы используете командлет **Get – MsolUser** без параметра _ALL_ , возвращаются только первые 500 учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="ed56a-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="ed56a-134">Чтобы отключить службы для группы существующих пользователей, воспользуйтесь одним из указанных ниже методов для идентификации пользователей.</span><span class="sxs-lookup"><span data-stu-id="ed56a-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="ed56a-135">**Способ 1. Фильтрация учетных записей на основе существующего атрибута учетной записи**</span><span class="sxs-lookup"><span data-stu-id="ed56a-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="ed56a-136">Для этого используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="ed56a-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="ed56a-137">В следующем примере отключаются службы для пользователей в отделе продаж в США.</span><span class="sxs-lookup"><span data-stu-id="ed56a-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="ed56a-138">**Способ 2: использование списка определенных учетных записей**</span><span class="sxs-lookup"><span data-stu-id="ed56a-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="ed56a-139">Для этого выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="ed56a-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="ed56a-140">Создайте текстовый файл, в котором в каждой строке будет по одной учетной записи, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="ed56a-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="ed56a-141">В этом примере текстовый файл имеет значение C:\\мои документы\\Accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="ed56a-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="ed56a-142">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="ed56a-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="ed56a-143">Если вы хотите отключить доступ к службам для нескольких планов лицензирования, повторите указанные выше инструкции для каждого плана лицензирования, убедившись в том, что:</span><span class="sxs-lookup"><span data-stu-id="ed56a-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="ed56a-144">Учетным записям пользователей назначен план лицензирования.</span><span class="sxs-lookup"><span data-stu-id="ed56a-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="ed56a-145">Службы, которые необходимо отключить, доступны в плане лицензирования.</span><span class="sxs-lookup"><span data-stu-id="ed56a-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="ed56a-146">Чтобы отключить службы Office 365 для пользователей при назначении их плану лицензирования, ознакомьтесь со статьей [Отключение доступа к службам при назначении пользовательских лицензий](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="ed56a-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="ed56a-147">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="ed56a-147">New to Office 365?</span></span>
<span data-ttu-id="ed56a-148"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="ed56a-148"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="ed56a-149">См. также</span><span class="sxs-lookup"><span data-stu-id="ed56a-149">See also</span></span>
<span data-ttu-id="ed56a-150"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="ed56a-150"></span></span>

<span data-ttu-id="ed56a-151">Сведения об управлении пользователями с помощью Office 365 PowerShell см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="ed56a-151">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="ed56a-152">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="ed56a-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ed56a-153">Удаление и восстановление учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="ed56a-153">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ed56a-154">Блокировка учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="ed56a-154">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ed56a-155">Назначение лицензий для учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="ed56a-155">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ed56a-156">Создание учетных записей пользователей с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="ed56a-156">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
