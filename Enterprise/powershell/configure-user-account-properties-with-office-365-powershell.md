---
title: Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
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
ms.openlocfilehash: 3d81a7e5860b086fd411e8e6fcaab44568e890d5
ms.sourcegitcommit: 4d29b00a57c22225f2cdd592064ee8b6e575fceb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "37411518"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="226f7-103">Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="226f7-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="226f7-104">**Сводка.** Настраивайте свойства учетных записей пользователей в клиенте Office 365, используя PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="226f7-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="226f7-105">Несмотря на то, что вы можете использовать центр администрирования Microsoft 365 для настройки свойств учетных записей пользователей клиента Office 365, вы также можете использовать PowerShell для Office 365 и выполнять некоторые действия, которые не могут находиться в центре администрирования.</span><span class="sxs-lookup"><span data-stu-id="226f7-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="226f7-106">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="226f7-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="226f7-107">Чтобы настроить свойства учетных записей пользователей с помощью модуля PowerShell Azure Active Directory для Graph, используйте командлет [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0), указав свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="226f7-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="226f7-108">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="226f7-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="226f7-109">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="226f7-109">Change properties for a specific user account</span></span>

<span data-ttu-id="226f7-p101">Параметр **-ObjectID** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="226f7-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="226f7-112">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="226f7-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="226f7-113">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="226f7-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="226f7-114">-FacsimilieTelephoneNumber "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="226f7-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="226f7-115">-GivenName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="226f7-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="226f7-116">-Surname "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="226f7-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="226f7-117">-Mobile "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="226f7-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="226f7-118">-JobTitle "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="226f7-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="226f7-119">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="226f7-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="226f7-120">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="226f7-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="226f7-121">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="226f7-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="226f7-122">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="226f7-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="226f7-123">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="226f7-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="226f7-124">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="226f7-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="226f7-125">-TelephoneNumber "\<номер рабочего телефона>"</span><span class="sxs-lookup"><span data-stu-id="226f7-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="226f7-126">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="226f7-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="226f7-127">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="226f7-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="226f7-128">Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="226f7-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>

>[!Note]
> <span data-ttu-id="226f7-129">Свойство **mail** задается с помощью параметра **– осермаилс** .</span><span class="sxs-lookup"><span data-stu-id="226f7-129">You set the **Mail** property with the **-OtherMails** parameter.</span></span>
>
 
<span data-ttu-id="226f7-130">Чтобы отобразить имя участника-пользователя для учетных записей пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="226f7-130">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="226f7-131">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="226f7-131">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="226f7-132">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-132">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-133">Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-133">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-134">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="226f7-134">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="226f7-135">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="226f7-135">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="226f7-p102">Эта команда возвращает список всех учетных записей. Если требуется показать имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), укажите значение переменной **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="226f7-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="226f7-138">В этом примере выводится имя участника-пользователя для учетной записи пользователя с отображаемым именем Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="226f7-138">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="226f7-p103">С помощью переменной **$upn** можно вносить изменения в учетные записи, указывая их отображаемые имена. В этом примере показано, как заменить текущее место работы пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="226f7-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="226f7-141">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="226f7-141">Change properties for all user accounts</span></span>

<span data-ttu-id="226f7-p104">Чтобы изменить свойства для всех пользователей, примените сочетание командлетов **Get-AzureADUser** и **Set-AzureADUser**. Следующий пример заменяет текущее расположение использования для всех пользователей на Францию:</span><span class="sxs-lookup"><span data-stu-id="226f7-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="226f7-144">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="226f7-144">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="226f7-145">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-145">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-146">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="226f7-146">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="226f7-147">Изменение свойств определенной части учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="226f7-147">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="226f7-p105">Сочетание командлетов **Get-AzureADUser**, **Where** и **Set-AzureADUser** позволит изменить свойства определенной части учетных записей пользователей. Следующая команда заменяет расположение всех пользователей в отделе Accounting на Францию:</span><span class="sxs-lookup"><span data-stu-id="226f7-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="226f7-150">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="226f7-150">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="226f7-151">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-151">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-152">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-152">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-153">Задать Францию в качестве расположения пользователя (**Set-AzureADUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="226f7-153">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="226f7-154">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="226f7-154">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="226f7-155">Чтобы настроить свойства учетных записей пользователей с помощью модуля Microsoft Azure Active Directory для Windows PowerShell, используйте командлет Set-MsolUser, указав свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="226f7-155">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="226f7-156">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="226f7-156">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="226f7-157">Изменение свойств учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="226f7-157">Change properties for a specific user account</span></span>

<span data-ttu-id="226f7-158">Чтобы настроить свойства учетной записи пользователя, используйте командлет [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) и укажите свойства, которые нужно задать или изменить.</span><span class="sxs-lookup"><span data-stu-id="226f7-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="226f7-p106">Параметр **-UserPrincipalName** указывает учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Ниже перечислены наиболее распространенные.</span><span class="sxs-lookup"><span data-stu-id="226f7-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="226f7-161">-City "\<название города>"</span><span class="sxs-lookup"><span data-stu-id="226f7-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="226f7-162">-Country "\<название страны>"</span><span class="sxs-lookup"><span data-stu-id="226f7-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="226f7-163">-Department "\<название отдела>"</span><span class="sxs-lookup"><span data-stu-id="226f7-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="226f7-164">-DisplayName "\<полное имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="226f7-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="226f7-165">-Fax "\<номер факса>"</span><span class="sxs-lookup"><span data-stu-id="226f7-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="226f7-166">-FirstName "\<имя пользователя>"</span><span class="sxs-lookup"><span data-stu-id="226f7-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="226f7-167">-LastName "\<фамилия пользователя>"</span><span class="sxs-lookup"><span data-stu-id="226f7-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="226f7-168">-MobilePhone "\<номер мобильного телефона>"</span><span class="sxs-lookup"><span data-stu-id="226f7-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="226f7-169">-Office "\<адрес офиса>"</span><span class="sxs-lookup"><span data-stu-id="226f7-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="226f7-170">-PhoneNumber "\<номер телефона офиса>"</span><span class="sxs-lookup"><span data-stu-id="226f7-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="226f7-171">-PostalCode "\<почтовый индекс>"</span><span class="sxs-lookup"><span data-stu-id="226f7-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="226f7-172">-PreferredLanguage "\<язык>"</span><span class="sxs-lookup"><span data-stu-id="226f7-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="226f7-173">-State "\<название штата>"</span><span class="sxs-lookup"><span data-stu-id="226f7-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="226f7-174">-StreetAddress "\<почтовый адрес>"</span><span class="sxs-lookup"><span data-stu-id="226f7-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="226f7-175">-Title "\<должность>"</span><span class="sxs-lookup"><span data-stu-id="226f7-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="226f7-176">-UsageLocation "\<2-значный код страны или региона>"</span><span class="sxs-lookup"><span data-stu-id="226f7-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="226f7-177">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="226f7-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="226f7-178">Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="226f7-178">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

>[!Note]
> <span data-ttu-id="226f7-179">Свойство **mail** задается с помощью параметра **– алтернатимаиладдрессес** .</span><span class="sxs-lookup"><span data-stu-id="226f7-179">You set the **Mail** property with the **-AlternateEmailAddresses** parameter.</span></span>
>
 
<span data-ttu-id="226f7-180">Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="226f7-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="226f7-181">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="226f7-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="226f7-182">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-183">Сортировать список имен участников-пользователей в алфавитном порядке (**Sort-Object UserPrincipalName**) и отправить его следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-184">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="226f7-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="226f7-185">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="226f7-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="226f7-p107">Эта команда вернет все учетные записи. Если нужно отобразить имя участника-пользователя для учетной записи по соответствующему отображаемому имени (имени и фамилии), введите переменную **$userName** ниже (удалив символы \< и >), а затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="226f7-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="226f7-188">Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="226f7-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="226f7-p108">С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="226f7-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="226f7-191">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="226f7-191">Change properties for all user accounts</span></span>

<span data-ttu-id="226f7-p109">Чтобы изменить свойства для всех пользователей, можно использовать сочетание командлетов **Get-MsolUser** и **Set-MsolUser**. В следующем примере место работы всех пользователей меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="226f7-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="226f7-194">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="226f7-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="226f7-195">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-196">Задать Францию в качестве расположения пользователя (**Set-MsolUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="226f7-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="226f7-197">Изменение свойств для определенного набора учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="226f7-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="226f7-p110">Сочетание командлетов **Get-MsolUser**, **Where-Object** и **Set-MsolUser** позволит изменить свойства для определенного набора учетных записей пользователей. Пример кода, приведенный ниже, заменяет текущее расположение использования для всех пользователей в отделе Accounting (бухгалтерского учета) на Францию.</span><span class="sxs-lookup"><span data-stu-id="226f7-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="226f7-200">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="226f7-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="226f7-201">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-202">Найти все учетные записи, в которых для свойства Department задано значение "Accounting" (**Where-Object {$_.Department -eq "Accounting"}**), и передать полученные сведения в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="226f7-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="226f7-203">Задать Францию в качестве расположения пользователя (**Set-MsolUser -UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="226f7-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="226f7-204">См. также</span><span class="sxs-lookup"><span data-stu-id="226f7-204">See also</span></span>

[<span data-ttu-id="226f7-205">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="226f7-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="226f7-206">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="226f7-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="226f7-207">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="226f7-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
