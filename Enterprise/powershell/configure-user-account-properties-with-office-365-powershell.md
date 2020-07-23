---
title: Настройка свойств учетной записи пользователя Microsoft 365 с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Сводка: использование PowerShell для Microsoft 365 для настройки свойств отдельных или нескольких учетных записей пользователей в клиенте Microsoft 365.'
ms.openlocfilehash: ccf9bf9930551ab1ee26ef7a1f69427cdc4871f5
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230855"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a><span data-ttu-id="fa5a1-103">Настройка свойств учетной записи пользователя Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa5a1-103">Configure Microsoft 365 user account properties with PowerShell</span></span>

<span data-ttu-id="fa5a1-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="fa5a1-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="fa5a1-105">Несмотря на то, что вы можете использовать центр администрирования Microsoft 365 для настройки свойств учетных записей пользователей клиента Microsoft 365, вы также можете использовать PowerShell и выполнить некоторые действия, которые не могут находиться в центре администрирования Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Microsoft 365 tenant, you can also use PowerShell and do some things that the Microsoft 365 admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fa5a1-106">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="fa5a1-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="fa5a1-107">Чтобы настроить свойства учетных записей пользователей с помощью модуля PowerShell Azure Active Directory для Graph, используйте командлет [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0), указав свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="fa5a1-108">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="fa5a1-109">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="fa5a1-109">Change properties for a specific user account</span></span>

<span data-ttu-id="fa5a1-p101">Параметр **-ObjectID** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="fa5a1-112">-Department "<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="fa5a1-113">-DisplayName "<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="fa5a1-114">-FacsimilieTelephoneNumber "<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="fa5a1-115">-GivenName "<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="fa5a1-116">-Surname "<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="fa5a1-117">-Mobile "<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="fa5a1-118">-JobTitle "<должность>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="fa5a1-119">-PreferredLanguage "<язык>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="fa5a1-120">-StreetAddress "<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="fa5a1-121">-City "<название города>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="fa5a1-122">-State "<название региона>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="fa5a1-123">-PostalCode "<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="fa5a1-124">-Country "<название страны>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="fa5a1-125">-TelephoneNumber "<номер рабочего телефона>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="fa5a1-126">— UsageLocation " \<2-character country or region code> "</span><span class="sxs-lookup"><span data-stu-id="fa5a1-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="fa5a1-127">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="fa5a1-128">Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="fa5a1-129">Чтобы отобразить имя участника-пользователя для учетных записей пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="fa5a1-130">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-130">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="fa5a1-131">Получите все сведения об учетных записях пользователей (**Get-AzureADUser**) и отправьте их в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-131">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-132">Сортировать список имен субъектов-пользователей в алфавитном порядке (**Сортировка userPrincipalName**) и отправлять их в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-132">Sort the list of User Principal Names alphabetically (**Sort UserPrincipalName**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-133">Отобразите только свойство имени участника-пользователя для каждой учетной записи (**выберите userPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-133">Display just the User Principal Name property for each account (**Select UserPrincipalName**).</span></span>

- <span data-ttu-id="fa5a1-134">Отобразить их на одном экране (**More**).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-134">Display them one screen at a time (**More**).</span></span>
    
<span data-ttu-id="fa5a1-135">Эта команда перечислит все учетные записи.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-135">This command will list all of your accounts.</span></span> <span data-ttu-id="fa5a1-136">Если вы хотите отобразить имя участника-пользователя для учетной записи на основе отображаемого имени (имя и фамилия), заполните приведенную ниже переменную **$username** (удалив \< and > символы), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fa5a1-137">В этом примере выводится имя участника-пользователя для учетной записи пользователя с отображаемым именем Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fa5a1-p103">С помощью переменной **$upn** можно вносить изменения в учетные записи, указывая их отображаемые имена. В этом примере показано, как заменить текущее место работы пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="fa5a1-140">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="fa5a1-140">Change properties for all user accounts</span></span>

<span data-ttu-id="fa5a1-p104">Чтобы изменить свойства для всех пользователей, примените сочетание командлетов **Get-AzureADUser** и **Set-AzureADUser**. Следующий пример заменяет текущее расположение использования для всех пользователей на Францию:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="fa5a1-143">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-143">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="fa5a1-144">Получите все сведения об учетных записях пользователей (**Get-AzureADUser**) и отправьте их в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-144">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-145">Задайте для расположения пользователя значение Франция (**Set-AzureADUser-UsageLocation "fr"**).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-145">Set the user location to France (**Set-AzureADUser -UsageLocation "FR"**).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="fa5a1-146">Изменение свойств определенной части учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="fa5a1-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="fa5a1-p105">Сочетание командлетов **Get-AzureADUser**, **Where** и **Set-AzureADUser** позволит изменить свойства определенной части учетных записей пользователей. Следующая команда заменяет расположение всех пользователей в отделе Accounting на Францию:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="fa5a1-149">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-149">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="fa5a1-150">Получите все сведения об учетных записях пользователей (**Get-AzureADUser**) и отправьте их в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-150">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-151">Найдите все учетные записи пользователей, для которых в свойстве Department задано значение "Accounting" (**где {$ _. Department-EQ "Accounting"}**) и отправьте полученные сведения в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-151">Find all of the user accounts that have their Department property set to "Accounting" (**Where {$_.Department -eq "Accounting"}**) and send the resulting information to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-152">Задайте для расположения пользователя значение Франция (**Set-AzureADUser-UsageLocation "fr"**).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-152">Set the user location to France (**Set-AzureADUser -UsageLocation "FR"**).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fa5a1-153">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa5a1-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fa5a1-154">Чтобы настроить свойства учетных записей пользователей с помощью модуля Microsoft Azure Active Directory для Windows PowerShell, используйте командлет **Set – MsolUser** и укажите свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="fa5a1-155">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-155">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="fa5a1-156">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="fa5a1-157">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="fa5a1-158">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="fa5a1-158">Change properties for a specific user account</span></span>

<span data-ttu-id="fa5a1-159">Чтобы настроить свойства учетной записи пользователя, используйте командлет [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) и укажите свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="fa5a1-p107">Параметр **-UserPrincipalName** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="fa5a1-162">-City "<название города>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="fa5a1-163">-Country "<название страны>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="fa5a1-164">-Department "<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="fa5a1-165">-DisplayName "<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="fa5a1-166">-Fax "<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="fa5a1-167">-FirstName "<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="fa5a1-168">-LastName "<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="fa5a1-169">-MobilePhone "<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="fa5a1-170">-Office "<расположение офиса>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="fa5a1-171">-PhoneNumber "<номер телефона офиса>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="fa5a1-172">-PostalCode "<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="fa5a1-173">-PreferredLanguage "<язык>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="fa5a1-174">-State "<название региона>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="fa5a1-175">-StreetAddress "<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="fa5a1-176">-Title "<должность>"</span><span class="sxs-lookup"><span data-stu-id="fa5a1-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="fa5a1-177">— UsageLocation " \<2-character country or region code> "</span><span class="sxs-lookup"><span data-stu-id="fa5a1-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="fa5a1-178">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="fa5a1-179">Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-179">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="fa5a1-180">Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="fa5a1-181">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-181">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="fa5a1-182">Получите все сведения об учетных записях пользователей (**Get-MsolUser**) и отправьте их в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-182">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-183">Сортировать список имен субъектов-пользователей в алфавитном порядке (**Сортировка userPrincipalName**) и отправлять их в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-183">Sort the list of User Principal Names alphabetically (**Sort UserPrincipalName**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-184">Отобразите только свойство имени участника-пользователя для каждой учетной записи (**выберите userPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-184">Display just the User Principal Name property for each account (**Select UserPrincipalName**).</span></span>
    
- <span data-ttu-id="fa5a1-185">Отобразить их на одном экране (**More**).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-185">Display them one screen at a time (**More**).</span></span>
    
<span data-ttu-id="fa5a1-186">Эта команда перечислит все учетные записи.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-186">This command will list all of your accounts.</span></span> <span data-ttu-id="fa5a1-187">Если вы хотите отобразить имя участника-пользователя для учетной записи на основе отображаемого имени (имя и фамилия), заполните приведенную ниже переменную **$username** (удалив \< and > символы), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-187">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fa5a1-188">Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fa5a1-p109">С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="fa5a1-191">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="fa5a1-191">Change properties for all user accounts</span></span>

<span data-ttu-id="fa5a1-p110">Чтобы изменить свойства для всех пользователей, можно использовать сочетание командлетов **Get-MsolUser** и **Set-MsolUser**. В следующем примере место работы всех пользователей меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="fa5a1-194">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-194">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="fa5a1-195">Получите все сведения об учетных записях пользователей (**Get-MsolUser**) и отправьте их в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-195">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-196">Задайте для расположения пользователя значение Франция (**Set-MsolUser-UsageLocation "fr"**).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-196">Set the user location to France (**Set-MsolUser -UsageLocation "FR"**).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="fa5a1-197">Изменение свойств для определенного набора учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="fa5a1-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="fa5a1-198">Чтобы изменить свойства для определенного набора учетных записей пользователей, можно использовать сочетание командлетов **Get – MsolUser**, **WHERE**и **Set — MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="fa5a1-198">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="fa5a1-199">Пример кода, приведенный ниже, заменяет текущее расположение использования для всех пользователей в отделе Accounting (бухгалтерского учета) на Францию.</span><span class="sxs-lookup"><span data-stu-id="fa5a1-199">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="fa5a1-200">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="fa5a1-200">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="fa5a1-201">Получите все сведения об учетных записях пользователей (**Get-MsolUser**) и отправьте их в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-201">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-202">Найдите все учетные записи пользователей, для которых в свойстве Department задано значение "Accounting" (**где {$ _. Department-EQ "Accounting"}**) и отправьте полученные сведения в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-202">Find all of the user accounts that have their Department property set to "Accounting" (**Where {$_.Department -eq "Accounting"}**) and send the resulting information to the next command (**|**).</span></span>
    
- <span data-ttu-id="fa5a1-203">Задайте для расположения пользователя значение Франция (**Set-MsolUser-UsageLocation "fr"**).</span><span class="sxs-lookup"><span data-stu-id="fa5a1-203">Set the user location to France (**Set-MsolUser -UsageLocation "FR"**).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="fa5a1-204">См. также</span><span class="sxs-lookup"><span data-stu-id="fa5a1-204">See also</span></span>

[<span data-ttu-id="fa5a1-205">Управление учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa5a1-205">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="fa5a1-206">Управление Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa5a1-206">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fa5a1-207">Начало работы с PowerShell для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="fa5a1-207">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
