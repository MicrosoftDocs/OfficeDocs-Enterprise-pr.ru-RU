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
ms.custom: O365ITProTrain, Ent_Office_Other, PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Сводка. Сведения о том, как с помощью PowerShell в Office 365 настроить свойства одной или нескольких учетных записей пользователей в клиенте Office 365:."
ms.openlocfilehash: 65857511886534e18ba3e67b79ab4d74a0119568
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="c2f09-103">Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="c2f09-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="c2f09-104">**Сводка.** Настраивайте свойства учетных записей пользователей в клиенте Office 365, используя PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="c2f09-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="c2f09-105">Хотя настраивать свойства учетных записей пользователей для клиента Office 365: можно и в Центре администрирования Office 365:, PowerShell в Office 365 позволяет выполнять задачи, не доступные в Центре администрирования Office 365:.</span><span class="sxs-lookup"><span data-stu-id="c2f09-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="c2f09-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="c2f09-106">Before you begin</span></span>

<span data-ttu-id="c2f09-p101">Для выполнения действий, описанных в этой статье, требуется подключение к PowerShell. Инструкции см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c2f09-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="c2f09-109">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="c2f09-109">Change properties for a specific user account</span></span>

<span data-ttu-id="c2f09-p102">Чтобы настроить свойства учетной записи пользователя, используйте командлет [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) и укажите свойства, которые нужно задать или изменить. Приведенная ниже команда меняет место работы пользователя Belinda Newman на Францию.</span><span class="sxs-lookup"><span data-stu-id="c2f09-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="c2f09-p103">Параметр **-UserPrincipalName** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="c2f09-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="c2f09-114">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="c2f09-115">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="c2f09-116">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="c2f09-117">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="c2f09-118">-Fax "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="c2f09-119">-FirstName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="c2f09-120">-LastName "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="c2f09-121">-MobilePhone "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="c2f09-122">-Office "\<адрес офиса>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="c2f09-123">-PhoneNumber "\<номер телефона офиса>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="c2f09-124">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="c2f09-125">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="c2f09-126">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="c2f09-127">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="c2f09-128">-Title "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="c2f09-129">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="c2f09-130">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="c2f09-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="c2f09-131">Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="c2f09-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="c2f09-132">Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="c2f09-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="c2f09-133">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="c2f09-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c2f09-134">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-135">Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-136">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="c2f09-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="c2f09-137">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="c2f09-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="c2f09-p104">Эта команда возвращает список всех учетных записей. Если требуется показать имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), укажите значение переменной **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="c2f09-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c2f09-140">В этом примере отображается имя участника-пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="c2f09-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c2f09-p105">С помощью переменной **$upn** можно вносить изменения в учетные записи, указывая их отображаемые имена. В этом примере показано, как заменить текущее место работы пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="c2f09-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="c2f09-143">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="c2f09-143">Change properties for all user accounts</span></span>

<span data-ttu-id="c2f09-p106">Чтобы изменить свойства всех пользователей, можно использовать сочетание командлетов **Get-MsolUser** и **Set-MsolUser**. В следующем примере место работы всех пользователей меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="c2f09-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="c2f09-146">Эта команда дает PowerShell следующее указание:</span><span class="sxs-lookup"><span data-stu-id="c2f09-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c2f09-147">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-148">Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="c2f09-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="c2f09-149">Изменение свойств для определенного набора учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="c2f09-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="c2f09-p107">Чтобы изменить свойства группы учетных записей пользователей, можно использовать сочетание командлетов **Get-MsolUser**, **Where-Object** и **Set-MsolUser**. В приведенном ниже примере кода текущее место работы всех пользователей в отделе Accounting (бухгалтерского учета) меняется на Францию.</span><span class="sxs-lookup"><span data-stu-id="c2f09-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="c2f09-152">Эта команда дает PowerShell следующее указание:</span><span class="sxs-lookup"><span data-stu-id="c2f09-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c2f09-153">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-154">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where-Object {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-155">Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="c2f09-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="c2f09-156">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="c2f09-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="c2f09-157">Как настроить свойства учетных записей пользователей с помощью модуля PowerShell для Azure Active Directory 2</span><span class="sxs-lookup"><span data-stu-id="c2f09-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="c2f09-p108">Чтобы настроить свойства учетных записей пользователей с помощью модуля Azure Active Directory версии 2 для PowerShell, выполните командлет [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0), указав свойства, которые нужно задать или изменить. Но сначала подключитесь к своей подписке. Инструкции см. в статье [Подключение к Office 365](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="c2f09-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="c2f09-161">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="c2f09-161">Change properties for a specific user account</span></span>

<span data-ttu-id="c2f09-162">Этот пример команды заменяет текущее расположение использования для пользователя Belinda Newman на Францию:</span><span class="sxs-lookup"><span data-stu-id="c2f09-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="c2f09-p109">Параметр **-ObjectID** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="c2f09-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="c2f09-165">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="c2f09-166">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="c2f09-167">-FacsimilieTelephoneNumber "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="c2f09-168">-GivenName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="c2f09-169">-Surname "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="c2f09-170">-Mobile "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="c2f09-171">-JobTitle "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="c2f09-172">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="c2f09-173">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="c2f09-174">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="c2f09-175">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="c2f09-176">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="c2f09-177">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="c2f09-178">-TelephoneNumber "\<номер рабочего телефона>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="c2f09-179">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="c2f09-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="c2f09-180">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="c2f09-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="c2f09-181">Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="c2f09-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="c2f09-182">Чтобы отобразить имя участника-пользователя для учетных записей пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="c2f09-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="c2f09-183">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="c2f09-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c2f09-184">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-185">Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-186">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="c2f09-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="c2f09-187">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="c2f09-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="c2f09-p110">Эта команда возвращает список всех учетных записей. Если требуется показать имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), укажите значение переменной **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="c2f09-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c2f09-190">В этом примере отображается имя участника-пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="c2f09-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c2f09-p111">С помощью переменной **$upn** можно вносить изменения в учетные записи, указывая их отображаемые имена. В этом примере показано, как заменить текущее место работы пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="c2f09-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="c2f09-193">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="c2f09-193">Change properties for all user accounts</span></span>

<span data-ttu-id="c2f09-p112">Чтобы изменить свойства всех пользователей, можно использовать сочетание командлетов **Get-AzureADUser** и **Set-AzureADUser**. В следующем примере текущее место работы всех пользователей меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="c2f09-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="c2f09-196">Эта команда дает PowerShell следующее указание:</span><span class="sxs-lookup"><span data-stu-id="c2f09-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c2f09-197">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-198">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="c2f09-199">Изменение свойств определенной части учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="c2f09-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="c2f09-p113">Чтобы изменить свойства группы учетных записей пользователей, можно использовать сочетание командлетов **Get-AzureADUser**, **Where** и **Set-AzureADUser**. В следующем примере место работы всех пользователей в отделе Accounting меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="c2f09-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="c2f09-202">Эта команда дает PowerShell следующее указание:</span><span class="sxs-lookup"><span data-stu-id="c2f09-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c2f09-203">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-204">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c2f09-205">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="c2f09-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="c2f09-206">См. также</span><span class="sxs-lookup"><span data-stu-id="c2f09-206">See also</span></span>

#### 

[<span data-ttu-id="c2f09-207">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2f09-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c2f09-208">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="c2f09-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c2f09-209">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2f09-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

