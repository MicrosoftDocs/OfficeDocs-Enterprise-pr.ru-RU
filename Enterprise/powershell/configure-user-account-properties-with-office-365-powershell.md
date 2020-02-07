---
title: Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Сводка. Сведения о том, как с помощью PowerShell в Office 365 настроить свойства одной или нескольких учетных записей пользователей в клиенте Office 365:.
ms.openlocfilehash: 211210dad54cb0af772af7dc611bc2c0fdf6035a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841606"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="52cc5-103">Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="52cc5-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="52cc5-104">Несмотря на то, что вы можете использовать центр администрирования Microsoft 365 для настройки свойств учетных записей пользователей клиента Office 365, вы также можете использовать PowerShell для Office 365 и выполнять некоторые действия, которые не могут находиться в центре администрирования.</span><span class="sxs-lookup"><span data-stu-id="52cc5-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="52cc5-105">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="52cc5-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="52cc5-106">Чтобы настроить свойства учетных записей пользователей с помощью модуля PowerShell Azure Active Directory для Graph, используйте командлет [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0), указав свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="52cc5-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="52cc5-107">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="52cc5-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="52cc5-108">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="52cc5-108">Change properties for a specific user account</span></span>

<span data-ttu-id="52cc5-p101">Параметр **-ObjectID** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="52cc5-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="52cc5-111">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="52cc5-112">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="52cc5-113">-FacsimilieTelephoneNumber "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="52cc5-114">-GivenName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="52cc5-115">-Surname "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="52cc5-116">-Mobile "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="52cc5-117">-JobTitle "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="52cc5-118">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="52cc5-119">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="52cc5-120">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="52cc5-121">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="52cc5-122">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="52cc5-123">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="52cc5-124">-TelephoneNumber "\<номер рабочего телефона>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="52cc5-125">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="52cc5-126">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="52cc5-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="52cc5-127">Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="52cc5-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="52cc5-128">Чтобы отобразить имя участника-пользователя для учетных записей пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="52cc5-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="52cc5-129">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="52cc5-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="52cc5-130">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-131">Сортировать список имен субъектов-пользователей в алфавитном порядке ( **Сортировка userPrincipalName** ) и отправлять их в следующую команду **|** ().</span><span class="sxs-lookup"><span data-stu-id="52cc5-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-132">Отобразите только свойство имени участника-пользователя для каждой учетной записи ( **выберите userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="52cc5-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="52cc5-133">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="52cc5-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="52cc5-p102">Эта команда возвращает список всех учетных записей. Если требуется показать имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), укажите значение переменной **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="52cc5-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="52cc5-136">В этом примере выводится имя участника-пользователя для учетной записи пользователя с отображаемым именем Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="52cc5-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="52cc5-p103">С помощью переменной **$upn** можно вносить изменения в учетные записи, указывая их отображаемые имена. В этом примере показано, как заменить текущее место работы пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="52cc5-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="52cc5-139">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="52cc5-139">Change properties for all user accounts</span></span>

<span data-ttu-id="52cc5-p104">Чтобы изменить свойства для всех пользователей, примените сочетание командлетов **Get-AzureADUser** и **Set-AzureADUser**. Следующий пример заменяет текущее расположение использования для всех пользователей на Францию:</span><span class="sxs-lookup"><span data-stu-id="52cc5-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="52cc5-142">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="52cc5-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="52cc5-143">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-144">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="52cc5-145">Изменение свойств определенной части учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="52cc5-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="52cc5-p105">Сочетание командлетов **Get-AzureADUser**, **Where** и **Set-AzureADUser** позволит изменить свойства определенной части учетных записей пользователей. Следующая команда заменяет расположение всех пользователей в отделе Accounting на Францию:</span><span class="sxs-lookup"><span data-stu-id="52cc5-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="52cc5-148">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="52cc5-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="52cc5-149">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-150">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-151">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="52cc5-152">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52cc5-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="52cc5-153">Чтобы настроить свойства учетных записей пользователей с помощью модуля Microsoft Azure Active Directory для Windows PowerShell, используйте командлет **Set – MsolUser** и укажите свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="52cc5-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="52cc5-154">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="52cc5-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="52cc5-155">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="52cc5-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="52cc5-156">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52cc5-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="52cc5-157">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="52cc5-157">Change properties for a specific user account</span></span>

<span data-ttu-id="52cc5-158">Чтобы настроить свойства учетной записи пользователя, используйте командлет [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) и укажите свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="52cc5-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="52cc5-p107">Параметр **-UserPrincipalName** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="52cc5-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="52cc5-161">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="52cc5-162">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="52cc5-163">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="52cc5-164">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="52cc5-165">-Fax "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="52cc5-166">-FirstName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="52cc5-167">-LastName "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="52cc5-168">-MobilePhone "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="52cc5-169">-Office "\<адрес офиса>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="52cc5-170">-PhoneNumber "\<номер телефона офиса>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="52cc5-171">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="52cc5-172">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="52cc5-173">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="52cc5-174">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="52cc5-175">-Title "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="52cc5-176">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="52cc5-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="52cc5-177">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="52cc5-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="52cc5-178">Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="52cc5-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="52cc5-179">Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="52cc5-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="52cc5-180">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="52cc5-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="52cc5-181">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-182">Сортировать список имен субъектов-пользователей в алфавитном порядке ( **Сортировка userPrincipalName** ) и отправлять их в следующую команду **|** ().</span><span class="sxs-lookup"><span data-stu-id="52cc5-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-183">Отобразите только свойство имени участника-пользователя для каждой учетной записи ( **выберите userPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="52cc5-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="52cc5-184">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="52cc5-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="52cc5-p108">Эта команда вернет все учетные записи. Если нужно отобразить имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), введите переменную **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="52cc5-p108">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="52cc5-187">Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="52cc5-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="52cc5-p109">С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="52cc5-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="52cc5-190">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="52cc5-190">Change properties for all user accounts</span></span>

<span data-ttu-id="52cc5-p110">Чтобы изменить свойства для всех пользователей, можно использовать сочетание командлетов **Get-MsolUser** и **Set-MsolUser**. В следующем примере место работы всех пользователей меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="52cc5-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="52cc5-193">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="52cc5-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="52cc5-194">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-195">Задать Францию в качестве расположения пользователя (**Set-MsolUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="52cc5-196">Изменение свойств для определенного набора учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="52cc5-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="52cc5-197">Чтобы изменить свойства для определенного набора учетных записей пользователей, можно использовать сочетание командлетов **Get – MsolUser**, **WHERE**и **Set — MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="52cc5-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="52cc5-198">Пример кода, приведенный ниже, заменяет текущее расположение использования для всех пользователей в отделе Accounting (бухгалтерского учета) на Францию.</span><span class="sxs-lookup"><span data-stu-id="52cc5-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="52cc5-199">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="52cc5-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="52cc5-200">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-201">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="52cc5-202">Задать Францию в качестве расположения пользователя (**Set-MsolUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="52cc5-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="52cc5-203">См. также</span><span class="sxs-lookup"><span data-stu-id="52cc5-203">See also</span></span>

[<span data-ttu-id="52cc5-204">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="52cc5-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="52cc5-205">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="52cc5-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="52cc5-206">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="52cc5-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
