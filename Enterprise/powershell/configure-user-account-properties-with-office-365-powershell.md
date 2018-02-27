---
title: "Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Сводка. Сведения о том, как с помощью PowerShell в Office 365 настроить свойства одной или нескольких учетных записей пользователей в клиенте Office 365:."
ms.openlocfilehash: 60b3c1d91df0cb28f19f60a285093de7337904a9
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="9bd6e-103">Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="9bd6e-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="9bd6e-104">**Сводка.** Настраивайте свойства учетных записей пользователей в клиенте Office 365, используя PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="9bd6e-105">Хотя настраивать свойства учетных записей пользователей для клиента Office 365: можно и в Центре администрирования Office 365:, PowerShell в Office 365 позволяет выполнять задачи, не доступные в Центре администрирования Office 365:.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="9bd6e-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="9bd6e-106">Before you begin</span></span>

<span data-ttu-id="9bd6e-p101">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="9bd6e-109">Изменение свойств для определенной учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="9bd6e-109">Change properties for a specific user account</span></span>

<span data-ttu-id="9bd6e-p102">Чтобы настроить свойства для определенной учетной записи пользователя, используйте командлет [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) и укажите свойства, которые нужно задать или изменить. Приведенный ниже пример команды меняет расположение использования для пользователя Belinda Newman, задавая Францию.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="9bd6e-p103">Параметр **-UserPrincipalName** позволяет определить учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Те из них, которые чаще всего используются, представлены ниже.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="9bd6e-114">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="9bd6e-115">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="9bd6e-116">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="9bd6e-117">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="9bd6e-118">-Fax "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="9bd6e-119">-FirstName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="9bd6e-120">-LastName "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="9bd6e-121">-MobilePhone "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="9bd6e-122">-Office "\<адрес офиса>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="9bd6e-123">-PhoneNumber "\<номер телефона офиса>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="9bd6e-124">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="9bd6e-125">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="9bd6e-126">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="9bd6e-127">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="9bd6e-128">-Title "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="9bd6e-129">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="9bd6e-130">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="9bd6e-131">Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="9bd6e-132">Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="9bd6e-133">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="9bd6e-134">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-135">Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-136">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="9bd6e-137">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="9bd6e-p104">Эта команда вернет все учетные записи. Если нужно отобразить имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), введите переменную **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="9bd6e-140">Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="9bd6e-p105">С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="9bd6e-143">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="9bd6e-143">Change properties for all user accounts</span></span>

<span data-ttu-id="9bd6e-p106">Чтобы изменить свойства для всех пользователей, можно использовать сочетание командлетов **Get-MsolUser** и **Set-MsolUser**. В следующем примере место работы всех пользователей меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="9bd6e-146">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="9bd6e-147">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-148">Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="9bd6e-149">Изменение свойств для определенного набора учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="9bd6e-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="9bd6e-p107">Сочетание командлетов **Get-MsolUser**, **Where-Object** и **Set-MsolUser** позволит изменить свойства для определенного набора учетных записей пользователей. Пример кода, приведенный ниже, заменяет текущее расположение использования для всех пользователей в отделе Accounting (бухгалтерского учета) на Францию.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="9bd6e-152">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="9bd6e-153">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-154">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where-Object {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-155">Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="9bd6e-156">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="9bd6e-157">Как настроить свойства учетных записей пользователей с помощью модуля PowerShell для Azure Active Directory 2</span><span class="sxs-lookup"><span data-stu-id="9bd6e-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="9bd6e-p108">Чтобы настроить свойства учетных записей пользователей с помощью модуля Azure Active Directory 2 для PowerShell, выполните командлет [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0), указав свойства, которые нужно задать или изменить. Но сначала подключитесь к своей подписке ([инструкции](https://go.microsoft.com/fwlink/?linkid=842218)).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="9bd6e-161">Изменение свойств для определенной учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="9bd6e-161">Change properties for a specific user account</span></span>

<span data-ttu-id="9bd6e-162">Этот пример команды заменяет текущее расположение использования для пользователя Belinda Newman на Францию:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="9bd6e-p109">Параметр **-ObjectID** позволяет определить учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Те из них, которые чаще всего используются, представлены ниже.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="9bd6e-165">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="9bd6e-166">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="9bd6e-167">-FacsimilieTelephoneNumber "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="9bd6e-168">-GivenName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="9bd6e-169">-Surname "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="9bd6e-170">-Mobile "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="9bd6e-171">-JobTitle "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="9bd6e-172">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="9bd6e-173">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="9bd6e-174">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="9bd6e-175">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="9bd6e-176">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="9bd6e-177">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="9bd6e-178">-TelephoneNumber "\<номер рабочего телефона>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="9bd6e-179">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="9bd6e-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="9bd6e-180">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="9bd6e-181">Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="9bd6e-182">Чтобы отобразить имя участника-пользователя для учетных записей пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="9bd6e-183">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="9bd6e-184">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-185">Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-186">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="9bd6e-187">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="9bd6e-p110">Эта команда вернет все учетные записи. Если нужно отобразить имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), введите переменную **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="9bd6e-190">Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="9bd6e-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="9bd6e-p111">С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="9bd6e-193">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="9bd6e-193">Change properties for all user accounts</span></span>

<span data-ttu-id="9bd6e-p112">Чтобы изменить свойства для всех пользователей, примените сочетание командлетов **Get-AzureADUser** и **Set-AzureADUser**. Следующий пример заменяет текущее расположение использования для всех пользователей на Францию:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="9bd6e-196">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="9bd6e-197">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-198">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="9bd6e-199">Изменение свойств определенной части учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="9bd6e-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="9bd6e-p113">Сочетание командлетов **Get-AzureADUser**, **Where** и **Set-AzureADUser** позволит изменить свойства определенной части учетных записей пользователей. Следующая команда заменяет расположение всех пользователей в отделе Accounting на Францию:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="9bd6e-202">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="9bd6e-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="9bd6e-203">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-204">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="9bd6e-205">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="9bd6e-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9bd6e-206">См. также</span><span class="sxs-lookup"><span data-stu-id="9bd6e-206">See also</span></span>

#### 

[<span data-ttu-id="9bd6e-207">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bd6e-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="9bd6e-208">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="9bd6e-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9bd6e-209">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bd6e-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

