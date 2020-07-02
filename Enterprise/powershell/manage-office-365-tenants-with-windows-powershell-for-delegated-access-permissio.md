---
title: Управление клиентами Microsoft 365 с помощью Windows PowerShell для партнеров с правами доступа к данным делегированного доступа
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Сводка: используйте Windows PowerShell для Microsoft 365 для управления клиентами клиенты.'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998235"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="a260e-103">Управление клиентами Microsoft 365 с помощью Windows PowerShell для партнеров с правами доступа к данным делегированного доступа</span><span class="sxs-lookup"><span data-stu-id="a260e-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="a260e-104">Windows PowerShell позволяет поставщикам синдикации и поставщикам облачных решений (CSP) легко администрировать и сообщать о параметрах аренды клиентов, недоступных в центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a260e-104">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="a260e-105">Обратите внимание на то, что для учетной записи администратора партнера для подключения к клиенты клиента требуется разрешение на администрирование от имени (АОБО).</span><span class="sxs-lookup"><span data-stu-id="a260e-105">Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="a260e-106">Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP).</span><span class="sxs-lookup"><span data-stu-id="a260e-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="a260e-107">Они часто бывают поставщиками сети или телекоммуникационных услуг в других компаниях.</span><span class="sxs-lookup"><span data-stu-id="a260e-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="a260e-108">Они объединяют подписки на Microsoft 365 на свои услуги своим клиентам.</span><span class="sxs-lookup"><span data-stu-id="a260e-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="a260e-109">Когда вы продаете подписку на Microsoft 365, им автоматически предоставляются разрешения на администрирование от имени пользователя (АОБО), чтобы они могли администрировать и предоставлять отчеты для клиентов клиенты.</span><span class="sxs-lookup"><span data-stu-id="a260e-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="a260e-110">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="a260e-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="a260e-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span><span class="sxs-lookup"><span data-stu-id="a260e-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span></span> <span data-ttu-id="a260e-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a260e-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="a260e-113">Вам также необходимы учетные данные администратора для клиента партнера.</span><span class="sxs-lookup"><span data-stu-id="a260e-113">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="a260e-114">Что нужно сделать</span><span class="sxs-lookup"><span data-stu-id="a260e-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="a260e-115">Список всех идентификаторов клиентов</span><span class="sxs-lookup"><span data-stu-id="a260e-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="a260e-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span><span class="sxs-lookup"><span data-stu-id="a260e-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span></span> <span data-ttu-id="a260e-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="a260e-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="a260e-118">Чтобы получить список всех идентификаторов пользовательских клиентов, к которым у вас есть доступ, выполните эту команду.</span><span class="sxs-lookup"><span data-stu-id="a260e-118">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="a260e-119">Отобразится список всех пользовательских клиентов по идентификатору **TenantId**.</span><span class="sxs-lookup"><span data-stu-id="a260e-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="a260e-120">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="a260e-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="a260e-121">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a260e-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="a260e-122">Получение идентификатора клиента по доменному имени</span><span class="sxs-lookup"><span data-stu-id="a260e-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="a260e-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span><span class="sxs-lookup"><span data-stu-id="a260e-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span></span> <span data-ttu-id="a260e-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span><span class="sxs-lookup"><span data-stu-id="a260e-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="a260e-125">Список всех доменов для клиента</span><span class="sxs-lookup"><span data-stu-id="a260e-125">List all domains for a tenant</span></span>

<span data-ttu-id="a260e-126">To get all domains for any one customer tenant, run this command.</span><span class="sxs-lookup"><span data-stu-id="a260e-126">To get all domains for any one customer tenant, run this command.</span></span> <span data-ttu-id="a260e-127">Replace  _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="a260e-127">Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="a260e-128">Если вы зарегистрировали дополнительные домены, будут возвращены все домены, связанные с **TenantId** пользователя.</span><span class="sxs-lookup"><span data-stu-id="a260e-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="a260e-129">Получение сопоставления всех клиентов и зарегистрированных доменов</span><span class="sxs-lookup"><span data-stu-id="a260e-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="a260e-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span><span class="sxs-lookup"><span data-stu-id="a260e-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span></span> <span data-ttu-id="a260e-131">This command generates a listing of all your customer tenant IDs and their domains.</span><span class="sxs-lookup"><span data-stu-id="a260e-131">This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="a260e-132">Получение всех пользователей для клиента</span><span class="sxs-lookup"><span data-stu-id="a260e-132">Get all users for a tenant</span></span>

<span data-ttu-id="a260e-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span><span class="sxs-lookup"><span data-stu-id="a260e-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span></span> <span data-ttu-id="a260e-134">Replace _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="a260e-134">Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="a260e-135">Получение всех сведений о пользователе</span><span class="sxs-lookup"><span data-stu-id="a260e-135">Get all details about a user</span></span>

<span data-ttu-id="a260e-136">If you want to see all the properties of a particular user, run this command.</span><span class="sxs-lookup"><span data-stu-id="a260e-136">If you want to see all the properties of a particular user, run this command.</span></span> <span data-ttu-id="a260e-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span><span class="sxs-lookup"><span data-stu-id="a260e-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="a260e-138">Добавление пользователей настройка параметров и назначение лицензий</span><span class="sxs-lookup"><span data-stu-id="a260e-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="a260e-139">Пакетное создание, Настройка и лицензирование пользователей Microsoft 365 особенно эффективны с помощью Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="a260e-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="a260e-140">В этом пошаговом процессе сначала создаются записи для всех пользователей, которых нужно добавить в файл значений с разделителями-запятыми (CSV), а затем импортируйте этот файл с помощью Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="a260e-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="a260e-141">Создание CSV-файла</span><span class="sxs-lookup"><span data-stu-id="a260e-141">Create a CSV file</span></span>

<span data-ttu-id="a260e-142">Создайте CSV-файл, используя следующий формат:</span><span class="sxs-lookup"><span data-stu-id="a260e-142">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="a260e-143">где:</span><span class="sxs-lookup"><span data-stu-id="a260e-143">where:</span></span>
  
- <span data-ttu-id="a260e-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span><span class="sxs-lookup"><span data-stu-id="a260e-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span></span> <span data-ttu-id="a260e-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span><span class="sxs-lookup"><span data-stu-id="a260e-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span></span> <span data-ttu-id="a260e-146">For example, the code for the United States is US, and the code for Brazil is BR.</span><span class="sxs-lookup"><span data-stu-id="a260e-146">For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="a260e-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span><span class="sxs-lookup"><span data-stu-id="a260e-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span></span> <span data-ttu-id="a260e-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span><span class="sxs-lookup"><span data-stu-id="a260e-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span></span> <span data-ttu-id="a260e-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span><span class="sxs-lookup"><span data-stu-id="a260e-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="a260e-150">Импорт CSV-файла и создание пользователей</span><span class="sxs-lookup"><span data-stu-id="a260e-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="a260e-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span><span class="sxs-lookup"><span data-stu-id="a260e-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span></span> <span data-ttu-id="a260e-152">Be sure to substitute the correct CSV file name.</span><span class="sxs-lookup"><span data-stu-id="a260e-152">Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="a260e-153">См. также</span><span class="sxs-lookup"><span data-stu-id="a260e-153">See also</span></span>

#### 

[<span data-ttu-id="a260e-154">Справка для партнеров</span><span class="sxs-lookup"><span data-stu-id="a260e-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

