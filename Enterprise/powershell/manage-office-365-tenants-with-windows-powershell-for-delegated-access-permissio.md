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
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Управление клиентами Microsoft 365 с помощью Windows PowerShell для партнеров с правами доступа к данным делегированного доступа

Windows PowerShell позволяет поставщикам синдикации и поставщикам облачных решений (CSP) легко администрировать и сообщать о параметрах аренды клиентов, недоступных в центре администрирования Microsoft 365. Обратите внимание на то, что для учетной записи администратора партнера для подключения к клиенты клиента требуется разрешение на администрирование от имени (АОБО).
  
Партнеры по делегированным правам доступа (DAP)  партнеры по синдикации и поставщики облачных решений (CSP). Они часто бывают поставщиками сети или телекоммуникационных услуг в других компаниях. Они объединяют подписки на Microsoft 365 на свои услуги своим клиентам. Когда вы продаете подписку на Microsoft 365, им автоматически предоставляются разрешения на администрирование от имени пользователя (АОБО), чтобы они могли администрировать и предоставлять отчеты для клиентов клиенты.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Что нужно знать перед началом работы?

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Вам также необходимы учетные данные администратора для клиента партнера.
  
## <a name="what-do-you-want-to-do"></a>Что нужно сделать

### <a name="list-all-tenant-ids"></a>Список всех идентификаторов клиентов

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
Чтобы получить список всех идентификаторов пользовательских клиентов, к которым у вас есть доступ, выполните эту команду.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

Отобразится список всех пользовательских клиентов по идентификатору **TenantId**.

>[!Note]
>В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени. Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Получение идентификатора клиента по доменному имени

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Список всех доменов для клиента

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Если вы зарегистрировали дополнительные домены, будут возвращены все домены, связанные с **TenantId** пользователя.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Получение сопоставления всех клиентов и зарегистрированных доменов

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Получение всех пользователей для клиента

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Получение всех сведений о пользователе

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Добавление пользователей настройка параметров и назначение лицензий

Пакетное создание, Настройка и лицензирование пользователей Microsoft 365 особенно эффективны с помощью Windows PowerShell для Office 365. В этом пошаговом процессе сначала создаются записи для всех пользователей, которых нужно добавить в файл значений с разделителями-запятыми (CSV), а затем импортируйте этот файл с помощью Windows PowerShell для Office 365. 
  
#### <a name="create-a-csv-file"></a>Создание CSV-файла

Создайте CSV-файл, используя следующий формат:
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
где:
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Импорт CSV-файла и создание пользователей

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>См. также

#### 

[Справка для партнеров](https://go.microsoft.com/fwlink/p/?LinkId=533477)

