---
title: Управление клиентами Office 365 с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: Сводка. Узнайте, как использовать Windows PowerShell для Office 365, чтобы управлять пользовательскими клиентами.
ms.openlocfilehash: f4c6f1a0275e9b483a30b31564426b62241029bf
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="b72e9-103">Управление клиентами Office 365 с помощью Windows PowerShell для партнеров службы разрешений делегированного доступа (DAP)</span><span class="sxs-lookup"><span data-stu-id="b72e9-103">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="b72e9-104">**Сводка.** Управляйте клиентами, используя Windows PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="b72e9-104">**Summary:** Use Windows PowerShell for Office 365 to manage your customer tenancies.</span></span>
  
<span data-ttu-id="b72e9-p101">Windows PowerShell позволяет партнерам поставщика облачных решений с легкостью администрировать параметры пользовательских областей клиентов, недоступные в Центре администрирования Office 365, а также создавать отчеты о них. Обратите внимание, что для подключения к пользовательским областям клиентов у партнерской учетной записи администратора должны быть разрешения "Администрирование от имени" (AOBO).</span><span class="sxs-lookup"><span data-stu-id="b72e9-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Office 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="b72e9-p102">Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP). Они часто бывают поставщиками услуг, связанных с сетью или телекоммуникацией, в других компаниях. Они внесли подписки на Office 365: в пакет своих услуг. Продавая подписки на Office 365:, они автоматически получают разрешения на администрирование от чьего-либо имени (AOBO) дляобласти клиентов пользователя, что позволяет им администрировать эти области и создавать отчеты.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="b72e9-111">Что нужно знать перед началом работы?</span><span class="sxs-lookup"><span data-stu-id="b72e9-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="b72e9-p103">Для процедур, описанных в этом разделе, требуется подключение к Windows PowerShell для Office 365:. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b72e9-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="b72e9-114">Вам также необходимы учетные данные администратора для клиента партнера.</span><span class="sxs-lookup"><span data-stu-id="b72e9-114">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="b72e9-115">Что нужно сделать</span><span class="sxs-lookup"><span data-stu-id="b72e9-115">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="b72e9-116">Список всех идентификаторов клиентов</span><span class="sxs-lookup"><span data-stu-id="b72e9-116">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="b72e9-p104">Если у вас более 500 клиентов, ограничьте область синтаксиса командлета параметром  _-All_ или _-MaxResultsParameter_. Это применимо и к другим командлетам, которые могут выдавать большое количество данных, например **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="b72e9-119">Чтобы получить список всех идентификаторов пользовательских клиентов, к которым у вас есть доступ, выполните эту команду.</span><span class="sxs-lookup"><span data-stu-id="b72e9-119">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object -TenantId
```

<span data-ttu-id="b72e9-120">Отобразится список всех пользовательских клиентов по идентификатору **TenantId**.</span><span class="sxs-lookup"><span data-stu-id="b72e9-120">This will display a listing of all your customer tenants by **TenantId**.</span></span>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="b72e9-121">Получение идентификатора клиента по доменному имени</span><span class="sxs-lookup"><span data-stu-id="b72e9-121">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="b72e9-p105">Чтобы получить **TenantId** определенного пользовательского клиента по доменному имени, выполните эту команду. Замените _<domainname.onmicrosoft.com>_ фактическим доменным именем нужного пользовательского клиента.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object -TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="b72e9-124">Список всех доменов для клиента</span><span class="sxs-lookup"><span data-stu-id="b72e9-124">List all domains for a tenant</span></span>

<span data-ttu-id="b72e9-p106">Чтобы получить все домены для любого пользовательского клиента, выполните эту команду. Замените  _<customer TenantId value>_ фактическим значением.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="b72e9-127">Если вы зарегистрировали дополнительные домены, будут возвращены все домены, связанные с **TenantId** пользователя.</span><span class="sxs-lookup"><span data-stu-id="b72e9-127">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="b72e9-128">Получение сопоставления всех клиентов и зарегистрированных доменов</span><span class="sxs-lookup"><span data-stu-id="b72e9-128">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="b72e9-p107">Предыдущие команды Windows PowerShell для Office 365: позволяют получить идентификаторы клиентов или домены, но не позволяют получить их одновременно и не показывают их сопоставление. Эта команда создает список всех идентификаторов пользовательских клиентов и их доменов.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p107">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="b72e9-131">Получение всех пользователей для клиента</span><span class="sxs-lookup"><span data-stu-id="b72e9-131">Get all users for a tenant</span></span>

<span data-ttu-id="b72e9-p108">Эта команда выведен на экран **UserPrincipalName**, **DisplayName** и состояние **isLicensed** для всех пользователей определенного клиента. Замените _<customer TenantId value>_ фактическим значением.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="b72e9-134">Получение всех сведений о пользователе</span><span class="sxs-lookup"><span data-stu-id="b72e9-134">Get all details about a user</span></span>

<span data-ttu-id="b72e9-p109">Чтобы увидеть все свойства определенного пользователя, выполните эту команду. Замените  _<customer TenantId value>_ и _<user principal name value>_ фактическими значениями.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="b72e9-137">Добавление пользователей настройка параметров и назначение лицензий</span><span class="sxs-lookup"><span data-stu-id="b72e9-137">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="b72e9-p110">Пакетное создание, настройка и лицензирование пользователей Office 365: особенно эффективны при использовании Windows PowerShell для Office 365:. В этом двухэтапном процессе сначала создаются записи для всех пользователей, которых нужно добавить, в файле с разделителями-запятыми (CSV), а затем этот файл импортируется с помощью Windows PowerShell для Office 365:.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p110">The bulk creation, configuration, and licensing of Office 365 users is particularly efficient by using Windows PowerShell for Office 365. In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="b72e9-140">Создание CSV-файла</span><span class="sxs-lookup"><span data-stu-id="b72e9-140">Create a CSV file</span></span>

<span data-ttu-id="b72e9-141">Создайте CSV-файл, используя следующий формат:</span><span class="sxs-lookup"><span data-stu-id="b72e9-141">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="b72e9-142">где:</span><span class="sxs-lookup"><span data-stu-id="b72e9-142">where:</span></span>
  
- <span data-ttu-id="b72e9-p111">**UsageLocation**. Это значение  двухбуквенный код страны или региона пользователя в формате ISO. Такие коды можно найти на сайте[веб-платформы сведений об ISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Например, код США  US, а Бразилии  BR.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="b72e9-p112">**LicenseAssignment**. Это значение имеет следующий формат: `syndication-account:<PROVISIONING_ID>`. Например, при назначении пользователям клиентов лицензий O365_Business_Premium значение **LicenseAssignment** имеет следующий вид: **syndication-account:O365_Business_Premium**. Идентификаторы PROVISIONING_ID можно найти на портале партнеров синдикации, к которому вы имеете доступ как партнер службы синдикации или CSP.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="b72e9-149">Импорт CSV-файла и создание пользователей</span><span class="sxs-lookup"><span data-stu-id="b72e9-149">Import the CSV file and create the users</span></span>

<span data-ttu-id="b72e9-p113">После создания CSV-файла выполните эту команду, чтобы создать учетные записи пользователей с бессрочными паролями, которые пользователи должны изменить при первом входе, и назначить им указанную лицензию. Не забудьте указать правильное имя CSV-файла.</span><span class="sxs-lookup"><span data-stu-id="b72e9-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="b72e9-152">См. также</span><span class="sxs-lookup"><span data-stu-id="b72e9-152">See also</span></span>

#### 

[<span data-ttu-id="b72e9-153">Справка для партнеров</span><span class="sxs-lookup"><span data-stu-id="b72e9-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

