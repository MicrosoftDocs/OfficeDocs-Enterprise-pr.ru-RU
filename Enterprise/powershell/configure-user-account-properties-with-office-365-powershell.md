---
title: Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Сводка. Сведения о том, как с помощью PowerShell в Office 365 настроить свойства одной или нескольких учетных записей пользователей в клиенте Office 365:.
ms.openlocfilehash: 53a99c33dcebebc87e12a468d56e5460b8a0c111
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782609"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="926b4-103">Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="926b4-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="926b4-104">**Сводка.** Настраивайте свойства учетных записей пользователей в клиенте Office 365, используя PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="926b4-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="926b4-105">Несмотря на то, что вы можете использовать центр администрирования Microsoft 365 для настройки свойств учетных записей пользователей клиента Office 365, вы также можете использовать PowerShell для Office 365 и выполнять некоторые действия, которые не могут находиться в центре администрирования.</span><span class="sxs-lookup"><span data-stu-id="926b4-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="926b4-106">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="926b4-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="926b4-107">Чтобы настроить свойства учетных записей пользователей с помощью модуля PowerShell Azure Active Directory для Graph, используйте командлет [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0), указав свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="926b4-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="926b4-108">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="926b4-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="926b4-109">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="926b4-109">Change properties for a specific user account</span></span>

<span data-ttu-id="926b4-p101">Параметр **-ObjectID** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="926b4-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="926b4-112">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="926b4-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="926b4-113">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="926b4-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="926b4-114">-FacsimilieTelephoneNumber "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="926b4-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="926b4-115">-GivenName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="926b4-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="926b4-116">-Surname "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="926b4-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="926b4-117">-Mobile "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="926b4-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="926b4-118">-JobTitle "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="926b4-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="926b4-119">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="926b4-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="926b4-120">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="926b4-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="926b4-121">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="926b4-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="926b4-122">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="926b4-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="926b4-123">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="926b4-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="926b4-124">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="926b4-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="926b4-125">-TelephoneNumber "\<номер рабочего телефона>"</span><span class="sxs-lookup"><span data-stu-id="926b4-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="926b4-126">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="926b4-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="926b4-127">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="926b4-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="926b4-128">Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="926b4-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="926b4-129">Чтобы отобразить имя участника-пользователя для учетных записей пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="926b4-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="926b4-130">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="926b4-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="926b4-131">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-132">Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-133">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="926b4-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="926b4-134">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="926b4-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="926b4-p102">Эта команда возвращает список всех учетных записей. Если требуется показать имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), укажите значение переменной **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="926b4-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="926b4-137">В этом примере выводится имя участника-пользователя для учетной записи пользователя с отображаемым именем Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="926b4-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="926b4-p103">С помощью переменной **$upn** можно вносить изменения в учетные записи, указывая их отображаемые имена. В этом примере показано, как заменить текущее место работы пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="926b4-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="926b4-140">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="926b4-140">Change properties for all user accounts</span></span>

<span data-ttu-id="926b4-p104">Чтобы изменить свойства для всех пользователей, примените сочетание командлетов **Get-AzureADUser** и **Set-AzureADUser**. Следующий пример заменяет текущее расположение использования для всех пользователей на Францию:</span><span class="sxs-lookup"><span data-stu-id="926b4-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="926b4-143">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="926b4-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="926b4-144">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-145">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="926b4-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="926b4-146">Изменение свойств определенной части учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="926b4-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="926b4-p105">Сочетание командлетов **Get-AzureADUser**, **Where** и **Set-AzureADUser** позволит изменить свойства определенной части учетных записей пользователей. Следующая команда заменяет расположение всех пользователей в отделе Accounting на Францию:</span><span class="sxs-lookup"><span data-stu-id="926b4-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="926b4-149">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="926b4-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="926b4-150">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-151">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-152">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="926b4-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="926b4-153">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="926b4-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="926b4-154">Чтобы настроить свойства учетных записей пользователей с помощью модуля Microsoft Azure Active Directory для Windows PowerShell, используйте командлет Set-MsolUser, указав свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="926b4-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="926b4-155">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="926b4-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="926b4-156">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="926b4-156">Change properties for a specific user account</span></span>

<span data-ttu-id="926b4-157">Чтобы настроить свойства учетной записи пользователя, используйте командлет [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) и укажите свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="926b4-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="926b4-p106">Параметр **-UserPrincipalName** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="926b4-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="926b4-160">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="926b4-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="926b4-161">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="926b4-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="926b4-162">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="926b4-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="926b4-163">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="926b4-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="926b4-164">-Fax "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="926b4-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="926b4-165">-FirstName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="926b4-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="926b4-166">-LastName "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="926b4-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="926b4-167">-MobilePhone "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="926b4-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="926b4-168">-Office "\<адрес офиса>"</span><span class="sxs-lookup"><span data-stu-id="926b4-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="926b4-169">-PhoneNumber "\<номер телефона офиса>"</span><span class="sxs-lookup"><span data-stu-id="926b4-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="926b4-170">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="926b4-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="926b4-171">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="926b4-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="926b4-172">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="926b4-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="926b4-173">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="926b4-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="926b4-174">-Title "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="926b4-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="926b4-175">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="926b4-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="926b4-176">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="926b4-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="926b4-177">Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="926b4-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="926b4-178">Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="926b4-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="926b4-179">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="926b4-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="926b4-180">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-181">Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-182">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="926b4-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="926b4-183">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="926b4-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="926b4-p107">Эта команда вернет все учетные записи. Если нужно отобразить имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), введите переменную **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="926b4-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="926b4-186">Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="926b4-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="926b4-p108">С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="926b4-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="926b4-189">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="926b4-189">Change properties for all user accounts</span></span>

<span data-ttu-id="926b4-p109">Чтобы изменить свойства для всех пользователей, можно использовать сочетание командлетов **Get-MsolUser** и **Set-MsolUser**. В следующем примере место работы всех пользователей меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="926b4-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="926b4-192">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="926b4-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="926b4-193">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-194">Задать Францию в качестве расположения пользователя (**Set-MsolUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="926b4-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="926b4-195">Изменение свойств для определенного набора учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="926b4-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="926b4-p110">Сочетание командлетов **Get-MsolUser**, **Where-Object** и **Set-MsolUser** позволит изменить свойства для определенного набора учетных записей пользователей. Пример кода, приведенный ниже, заменяет текущее расположение использования для всех пользователей в отделе Accounting (бухгалтерского учета) на Францию.</span><span class="sxs-lookup"><span data-stu-id="926b4-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="926b4-198">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="926b4-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="926b4-199">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-200">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where-Object {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="926b4-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="926b4-201">Задать Францию в качестве расположения пользователя (**Set-MsolUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="926b4-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="926b4-202">См. также</span><span class="sxs-lookup"><span data-stu-id="926b4-202">See also</span></span>

[<span data-ttu-id="926b4-203">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="926b4-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="926b4-204">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="926b4-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="926b4-205">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="926b4-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
