---
title: Просмотр сведений о лицензии и службе учетной записи Microsoft 365 с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: В этой статье объясняется, как определить службы Microsoft 365, назначенные пользователям, с помощью PowerShell.
ms.openlocfilehash: 73af2fd40df8b36507250edcef48359e9d555a7f
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230245"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a><span data-ttu-id="07060-103">Просмотр сведений о лицензии и службе учетной записи Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="07060-103">View Microsoft 365 account license and service details with PowerShell</span></span>

<span data-ttu-id="07060-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="07060-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="07060-105">В Microsoft 365 лицензии из планов лицензирования (также называемых конфигурациями и планами Microsoft 365) предоставляют пользователям доступ к службам Microsoft 365, определенным для этих планов.</span><span class="sxs-lookup"><span data-stu-id="07060-105">In Microsoft 365, licenses from licensing plans (also called SKUs or Microsoft 365 plans) give users access to the Microsoft 365 services that are defined for those plans.</span></span> <span data-ttu-id="07060-106">Однако у пользователя могут отсутствовать права на доступ ко всем службам, которые доступны в лицензии, назначенной им в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="07060-106">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="07060-107">Для просмотра состояния служб на учетных записях пользователей можно использовать PowerShell для Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="07060-107">You can use PowerShell for Microsoft 365 to view the status of services on user accounts.</span></span> 

<span data-ttu-id="07060-108">Для получения дополнительных сведений о планах лицензирования, лицензиях и службах ознакомьтесь со статьей [Просмотр лицензий и служб с помощью PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="07060-108">For more information about licensing plans, license, and services, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="07060-109">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="07060-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="07060-110">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="07060-110">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="07060-111">Затем перечислите план лицензирования для клиента с помощью этой команды.</span><span class="sxs-lookup"><span data-stu-id="07060-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="07060-112">Используйте эти команды для перечисления служб, доступных в каждом плане лицензирования.</span><span class="sxs-lookup"><span data-stu-id="07060-112">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="07060-113">Используйте эти команды для перечисления лицензий, назначенных учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="07060-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="07060-114">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="07060-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="07060-115">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="07060-115">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="07060-116">Затем выполните эту команду, чтобы получить список планов лицензирования, доступных в Организации.</span><span class="sxs-lookup"><span data-stu-id="07060-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="07060-117">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="07060-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="07060-118">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07060-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="07060-119">Затем выполните эту команду, чтобы получить список служб, доступных в каждом плане лицензирования, и порядок, в котором они указаны (номер индекса).</span><span class="sxs-lookup"><span data-stu-id="07060-119">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
<span data-ttu-id="07060-120">Используйте эту команду, чтобы получить список лицензий, назначенных пользователю, и порядок их следования (номер индекса).</span><span class="sxs-lookup"><span data-stu-id="07060-120">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="07060-121">Просмотр служб для учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="07060-121">To view services for a user account</span></span>

<span data-ttu-id="07060-122">Чтобы просмотреть все службы Microsoft 365, к которым у пользователя есть доступ, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="07060-122">To view all the Microsoft 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="07060-123">В этом примере показаны службы, к которым у пользователя BelindaN@litwareinc.com есть доступ.</span><span class="sxs-lookup"><span data-stu-id="07060-123">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="07060-124">Этот код показывает службы, связанные со всеми лицензиями, назначенными ее учетной записи.</span><span class="sxs-lookup"><span data-stu-id="07060-124">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="07060-125">Этот код показывает службы, к которым у пользователя BelindaN@litwareinc.com есть доступ по первой назначенной ей лицензии (индекс 0).</span><span class="sxs-lookup"><span data-stu-id="07060-125">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="07060-126">Чтобы просмотреть все службы для пользователя, которому назначено *несколько лицензий*, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="07060-126">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="07060-127">См. также</span><span class="sxs-lookup"><span data-stu-id="07060-127">See also</span></span>

[<span data-ttu-id="07060-128">Управление учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="07060-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="07060-129">Управление Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="07060-129">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="07060-130">Начало работы с PowerShell для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="07060-130">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
