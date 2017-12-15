---
title: "Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365"
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
- DecEntMigration
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Сводка. Сведения о том, как с помощью PowerShell в Office 365 настроить свойства одной или нескольких учетных записей пользователей в клиенте Office 365:."
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="ceebe-103">Настройка параметров учетной записи пользователя с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="ceebe-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="ceebe-104">**Сводка:** Использование Office 365 PowerShell для настройки свойств из одного или нескольких учетных записей пользователей в клиент Office 365.</span><span class="sxs-lookup"><span data-stu-id="ceebe-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="ceebe-105">Хотя настраивать свойства учетных записей пользователей для клиента Office 365: можно и в Центре администрирования Office 365:, PowerShell в Office 365 позволяет выполнять задачи, не доступные в Центре администрирования Office 365:.</span><span class="sxs-lookup"><span data-stu-id="ceebe-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="ceebe-106">Приступая к работе</span><span class="sxs-lookup"><span data-stu-id="ceebe-106">Before you begin</span></span>

<span data-ttu-id="ceebe-p101">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ceebe-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="ceebe-109">Изменение свойств для определенной учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="ceebe-109">Change properties for a specific user account</span></span>

<span data-ttu-id="ceebe-p102">Чтобы настроить свойства для определенной учетной записи пользователя, используйте командлет [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) и укажите свойства, которые нужно задать или изменить. Приведенный ниже пример команды меняет расположение использования для пользователя Belinda Newman, задавая Францию.</span><span class="sxs-lookup"><span data-stu-id="ceebe-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="ceebe-p103">Параметр **-UserPrincipalName** позволяет определить учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Те из них, которые чаще всего используются, представлены ниже.</span><span class="sxs-lookup"><span data-stu-id="ceebe-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="ceebe-114">-Город "\<название города >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="ceebe-115">-Страна "\<название страны >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="ceebe-116">-Department "\<имя отдела >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="ceebe-117">-DisplayName "\<полное имя пользователя >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="ceebe-118">-Факс "\<номер факса >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="ceebe-119">-FirstName "\<имя пользователя >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="ceebe-120">-LastName "\<Фамилия пользователя >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="ceebe-121">-MobilePhone "\<номер мобильного телефона >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="ceebe-122">— Office "\<расположение комнаты >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="ceebe-123">-PhoneNumber "\<office номер телефона >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="ceebe-124">-PostalCode "\<почтовый индекс >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="ceebe-125">-PreferredLanguage "\<язык >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="ceebe-126">-Состояние "\<имя состояния >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="ceebe-127">Улица-"\<почтовый адрес >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="ceebe-128">-Title "\<имя заголовка >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="ceebe-129">-UsageLocation "\<2-символьный код страны или региона >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="ceebe-130">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="ceebe-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="ceebe-131">Сведения о дополнительных параметрах см. в статье [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="ceebe-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="ceebe-132">Чтобы просмотреть имя участника-пользователя для каждого из пользователей, выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="ceebe-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="ceebe-133">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="ceebe-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ceebe-134">Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-135">Сортировка списка имена участника-пользователя ( **UserPrincipalName Sort-Object** ) и отправьте его в следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-136">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="ceebe-137">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="ceebe-p104">Эта команда выводит список всех учетных записей. Если вы хотите отобразить имя участника-пользователя для учетной записи на основании его отображения name (имя и фамилию), заполните поля в переменной **$userName** ниже (удаление \< и > символов), и затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="ceebe-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ceebe-140">Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="ceebe-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ceebe-p105">С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="ceebe-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="ceebe-143">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="ceebe-143">Change properties for all user accounts</span></span>

<span data-ttu-id="ceebe-p106">Чтобы изменить свойства для всех пользователей, можно использовать сочетание командлетов **Get-MsolUser** и **Set-MsolUser**. В следующем примере место работы всех пользователей меняется на Францию:</span><span class="sxs-lookup"><span data-stu-id="ceebe-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="ceebe-146">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="ceebe-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ceebe-147">Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-148">Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="ceebe-149">Изменение свойств для определенного набора учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="ceebe-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="ceebe-p107">Сочетание командлетов **Get-MsolUser**, **Where-Object** и **Set-MsolUser** позволит изменить свойства для определенного набора учетных записей пользователей. Пример кода, приведенный ниже, заменяет текущее расположение использования для всех пользователей в отделе Accounting (бухгалтерского учета) на Францию.</span><span class="sxs-lookup"><span data-stu-id="ceebe-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="ceebe-152">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="ceebe-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ceebe-153">Получение всех данных на учетные записи пользователей ( **Такую** ) и отправьте его в следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-154">Найти все учетные записи пользователей, которые имеют отдела свойство присвоено значение «Accounting» ( **Where-Object {$_. Отдел - eq «Учет»}** ) и отправлять полученные сведения к следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-155">Задать Францию в качестве места работы ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="ceebe-156">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="ceebe-157">Как настроить свойства учетных записей пользователей с помощью модуля PowerShell для Azure Active Directory 2</span><span class="sxs-lookup"><span data-stu-id="ceebe-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="ceebe-p108">Чтобы настроить свойства для учетных записей пользователей с помощью модуля Azure Active Directory версии 2 PowerShell, с помощью командлета [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) и укажите свойства для задания или изменения. Но для начала необходимо подключиться к своей подписке. Инструкции в разделе [подключение с помощью модуля Azure Active Directory версии 2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="ceebe-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="ceebe-161">Изменение свойств для определенной учетной записи пользователя</span><span class="sxs-lookup"><span data-stu-id="ceebe-161">Change properties for a specific user account</span></span>

<span data-ttu-id="ceebe-162">Этот пример команды заменяет текущее расположение использования для пользователя Belinda Newman на Францию:</span><span class="sxs-lookup"><span data-stu-id="ceebe-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="ceebe-p109">Параметр **-ObjectID** позволяет определить учетную запись, а ее свойства можно задать или изменить с помощью дополнительных параметров. Те из них, которые чаще всего используются, представлены ниже.</span><span class="sxs-lookup"><span data-stu-id="ceebe-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="ceebe-165">-Department "\<имя отдела >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="ceebe-166">-DisplayName "\<полное имя пользователя >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="ceebe-167">-FacsimilieTelephoneNumber "\<номер факса >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="ceebe-168">-GivenName "\<имя пользователя >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="ceebe-169">-Фамилия "\<Фамилия пользователя >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="ceebe-170">-Мобильных устройств "\<номер мобильного телефона >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="ceebe-171">— Название должности "\<должность >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="ceebe-172">-PreferredLanguage "\<язык >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="ceebe-173">Улица-"\<почтовый адрес >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="ceebe-174">-Город "\<название города >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="ceebe-175">-Состояние "\<имя состояния >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="ceebe-176">-PostalCode "\<почтовый индекс >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="ceebe-177">-Страна "\<название страны >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="ceebe-178">-TelephoneNumber "\<office номер телефона >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="ceebe-179">-UsageLocation "\<2-символьный код страны или региона >»</span><span class="sxs-lookup"><span data-stu-id="ceebe-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="ceebe-180">Это двухбуквенный код страны или региона согласно ISO 3166-1 alpha-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="ceebe-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="ceebe-181">Сведения о дополнительных параметрах см. в статье [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="ceebe-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="ceebe-182">Для отображения имени участника-пользователя для учетные записи пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="ceebe-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="ceebe-183">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="ceebe-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ceebe-184">Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-185">Сортировка списка имена участника-пользователя ( **UserPrincipalName Sort-Object** ) и отправьте его в следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-186">Отобразить только свойство имени участника-пользователя для каждой учетной записи ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="ceebe-187">Отобразить их на одном экране ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="ceebe-p110">Эта команда выводит список всех учетных записей. Если вы хотите отобразить имя участника-пользователя для учетной записи на основании его отображения name (имя и фамилию), заполните поля в переменной **$userName** ниже (удаление \< и > символов), и затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="ceebe-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ceebe-190">Этот пример отображает имя участника-пользователя для пользователя Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="ceebe-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ceebe-p111">С помощью переменной **$upn** можно вносить изменения в отдельные учетные записи с учетом их отображаемых имен. Данный пример показывает, как заменить текущее расположение использования для пользователя Belinda Newman на Францию, указав при этом соответствующее отображаемое имя, а не имя участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="ceebe-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="ceebe-193">Изменение свойств для всех учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="ceebe-193">Change properties for all user accounts</span></span>

<span data-ttu-id="ceebe-p112">Чтобы изменить свойства для всех пользователей, примените сочетание командлетов **Get-AzureADUser** и **Set-AzureADUser**. Следующий пример заменяет текущее расположение использования для всех пользователей на Францию:</span><span class="sxs-lookup"><span data-stu-id="ceebe-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="ceebe-196">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="ceebe-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ceebe-197">Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-198">Задать Францию в качестве расположения пользователя ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="ceebe-199">Изменение свойств для определенного набора учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="ceebe-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="ceebe-p113">Чтобы изменить свойства для определенного набора учетная запись пользователя, можно использовать сочетание командлеты **Get-AzureADUser**, **где**и **Set-AzureADUser** . В следующем примере изменяется местоположение об использовании для всех пользователей в бухгалтерии для Франции:</span><span class="sxs-lookup"><span data-stu-id="ceebe-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="ceebe-202">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="ceebe-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ceebe-203">Получение всех данных на учетные записи пользователей ( **Get-AzureADUser** ) и отправьте его в следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-204">Найти все учетные записи пользователей, которые имеют свойство отдела присвоено значение «Accounting» ( **где {$_. Отдел - eq «Учет»}** ) и отправлять полученные сведения к следующей команде ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ceebe-205">Задать Францию в качестве расположения пользователя ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="ceebe-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="ceebe-206">See also</span><span class="sxs-lookup"><span data-stu-id="ceebe-206">See also</span></span>

#### 

[<span data-ttu-id="ceebe-207">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ceebe-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ceebe-208">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="ceebe-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ceebe-209">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ceebe-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

