---
title: Просмотр учетных записей пользователей Microsoft 365 с помощью PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Сводка: Просмотр, список или отображение учетных записей пользователей Microsoft 365 различными способами с помощью PowerShell.'
ms.openlocfilehash: a67457169328828b2b471dd5db6a53bab3bbacda
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230205"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="596b5-103">Просмотр учетных записей пользователей Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="596b5-103">View Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="596b5-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="596b5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="596b5-105">Несмотря на то, что вы можете использовать центр администрирования Microsoft 365 для просмотра учетных записей клиента Microsoft 365, вы также можете использовать PowerShell для Microsoft 365 и выполнять некоторые действия, которые не могут находиться в центре администрирования.</span><span class="sxs-lookup"><span data-stu-id="596b5-105">Although you can use the Microsoft 365 admin center to view the accounts for your Microsoft 365 tenant, you can also use PowerShell for Microsoft 365 and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="596b5-106">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="596b5-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="596b5-107">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="596b5-107">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="596b5-108">Просмотр всех учетных записей</span><span class="sxs-lookup"><span data-stu-id="596b5-108">View all accounts</span></span>

<span data-ttu-id="596b5-109">Чтобы отобразить полный список учетных записей пользователей, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="596b5-109">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="596b5-110">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="596b5-110">You should see information similar to this:</span></span>
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="596b5-111">Просмотр определенной учетной записи</span><span class="sxs-lookup"><span data-stu-id="596b5-111">View a specific account</span></span>

<span data-ttu-id="596b5-112">Чтобы отобразить определенную учетную запись пользователя, введите имя учетной записи пользователя, также называемое именем участника-пользователя (UPN), удалите символы "<" и ">", а затем выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="596b5-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="596b5-113">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="596b5-113">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="596b5-114">Просмотр дополнительных значений свойств для конкретной учетной записи</span><span class="sxs-lookup"><span data-stu-id="596b5-114">View additional property values for a specific account</span></span>

<span data-ttu-id="596b5-115">По умолчанию командлет **Get – AzureADUser** отображает свойства ObjectID, DisplayName и userPrincipalName для учетных записей.</span><span class="sxs-lookup"><span data-stu-id="596b5-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="596b5-116">Чтобы сделать более избирательным список отображаемых свойств, можно использовать командлет **SELECT** в сочетании с командлетом **Get – AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="596b5-116">To be more selective about the list of properties to display, you can use the **Select** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="596b5-117">Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который сообщает PowerShell Active Directory PowerShell для Graph, чтобы получить результаты одной команды и отправить ее следующей команде.</span><span class="sxs-lookup"><span data-stu-id="596b5-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="596b5-118">Ниже приведен пример команды, которая отображает DisplayName, Department и UsageLocation для каждой учетной записи пользователя:</span><span class="sxs-lookup"><span data-stu-id="596b5-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

<span data-ttu-id="596b5-119">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="596b5-119">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="596b5-120">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="596b5-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="596b5-121">Отображение только имени, отдела и места использования учетной записи пользователя ( **выберите DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-121">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="596b5-122">Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **SELECT** и подстановочный знак (\*), чтобы отображать их все для конкретной учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="596b5-122">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="596b5-123">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="596b5-123">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="596b5-124">В качестве другого примера можно проверить включенное состояние конкретной учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="596b5-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="596b5-125">Просмотр некоторых учетных записей на основе общего свойства</span><span class="sxs-lookup"><span data-stu-id="596b5-125">View some accounts based on a common property</span></span>

<span data-ttu-id="596b5-126">Чтобы сделать более избирательным список отображаемых учетных записей, можно использовать командлет **WHERE** в сочетании с командлетом **Get – AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="596b5-126">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="596b5-127">Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который сообщает PowerShell Active Directory PowerShell для Graph, чтобы получить результаты одной команды и отправить ее следующей команде.</span><span class="sxs-lookup"><span data-stu-id="596b5-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="596b5-128">Ниже приведен пример команды, которая выводит только учетные записи, для которых не указано место использования:</span><span class="sxs-lookup"><span data-stu-id="596b5-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="596b5-129">Эта команда указывает Azure Active Directory PowerShell для Graph:</span><span class="sxs-lookup"><span data-stu-id="596b5-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="596b5-130">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="596b5-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="596b5-131">Найдите все учетные записи пользователей с незаданной областью использования ( **где {$ \_ . UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-131">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="596b5-132">В фигурных скобках команда предписывает PowerShell только искать набор учетных записей, в которых свойство учетной записи пользователя UsageLocation ( \*\* $ \_ . UsageLocation\*\* ) не указан ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-132">Inside the braces, the command instructs PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="596b5-133">**UsageLocation** — лишь одно из многих свойств, связанных с учетной записью пользователя.</span><span class="sxs-lookup"><span data-stu-id="596b5-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="596b5-134">Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **SELECT** и подстановочный знак (\*), чтобы отображать их все для конкретной учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="596b5-134">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="596b5-135">Пример:</span><span class="sxs-lookup"><span data-stu-id="596b5-135">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="596b5-p106">Например, **City** для этого списка — имя свойства, принадлежащего учетной записи пользователя. Это значит, что перечислить все учетные записи пользователей, проживающих в Лондоне, можно с помощью такой команды:</span><span class="sxs-lookup"><span data-stu-id="596b5-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="596b5-138">В приведенных ниже примерах используется синтаксис для командлета **WHERE** **{$ \_ .**</span><span class="sxs-lookup"><span data-stu-id="596b5-138">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="596b5-139">[имя свойства учетной записи пользователя] [оператор сравнения] оно **}**. > [оператор сравнения] имеет значение **-EQ** для Equals, **-Ne** для Not Equals, **-lt** для "меньше, чем", "-gt" для "больше чем", " **-gt** " и других.</span><span class="sxs-lookup"><span data-stu-id="596b5-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="596b5-140">[Value] как правило, это строка (последовательность букв, цифр и других знаков), числовое значение или **$null** для незаданных> узнать, [где](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) можно получить дополнительные сведения.</span><span class="sxs-lookup"><span data-stu-id="596b5-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="596b5-141">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="596b5-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="596b5-142">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="596b5-142">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="596b5-143">Просмотр всех учетных записей</span><span class="sxs-lookup"><span data-stu-id="596b5-143">View all accounts</span></span>

<span data-ttu-id="596b5-144">Чтобы отобразить полный список учетных записей пользователей, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="596b5-144">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="596b5-145">В PowerShell Core не поддерживается модуль Microsoft Azure Active Directory для Windows PowerShell и командлеты с компонентом **Msol** в имени.</span><span class="sxs-lookup"><span data-stu-id="596b5-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="596b5-146">Чтобы использовать эти командлеты, необходимо запустить их из Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="596b5-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="596b5-147">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="596b5-147">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="596b5-148">У командлета **Get-MsolUser** также есть ряд параметров для фильтрации отображаемых учетных данных.</span><span class="sxs-lookup"><span data-stu-id="596b5-148">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="596b5-149">Например, чтобы получить список нелицензированных пользователей (пользователей, добавленных в Microsoft 365, но еще не лицензированных для использования каких-либо служб), выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="596b5-149">For example, for the list of unlicensed users (users who've been added to Microsoft 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="596b5-150">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="596b5-150">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="596b5-151">Дополнительные сведения о дополнительных параметрах для фильтрации отображаемого набора учетных записей пользователей приведены в статье [Get – MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="596b5-151">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  
### <a name="view-a-specific-account"></a><span data-ttu-id="596b5-152">Просмотр определенной учетной записи</span><span class="sxs-lookup"><span data-stu-id="596b5-152">View a specific account</span></span>

<span data-ttu-id="596b5-153">Чтобы отобразить определенную учетную запись пользователя, введите учетную запись пользователя учетной записи пользователя, которая также называется именем участника-пользователя (UPN), удалите символы "<" и ">", а затем выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="596b5-153">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="596b5-154">Просмотр некоторых учетных записей на основе общего свойства</span><span class="sxs-lookup"><span data-stu-id="596b5-154">View some accounts based on a common property</span></span>

<span data-ttu-id="596b5-155">Чтобы сделать более избирательным список отображаемых учетных записей, можно использовать командлет **WHERE** в сочетании с командлетом **Get – MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="596b5-155">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="596b5-156">Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который указывает PowerShell на получение результатов одной команды и их отправку в следующую команду.</span><span class="sxs-lookup"><span data-stu-id="596b5-156">To combine the two cmdlets, we use the "pipe" character "|", which tells PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="596b5-157">Ниже приведен пример команды, которая выводит только учетные записи, для которых не указано место использования:</span><span class="sxs-lookup"><span data-stu-id="596b5-157">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="596b5-158">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="596b5-158">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="596b5-159">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="596b5-159">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="596b5-160">Найдите все учетные записи пользователей с незаданной областью использования ( **где {$ \_ . UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-160">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="596b5-161">В фигурных скобках команда предписывает PowerShell только искать набор учетных записей, в которых свойство учетной записи пользователя UsageLocation ( \*\* $ \_ . UsageLocation\*\* ) не указан ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-161">Inside the braces, the command instructs PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="596b5-162">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="596b5-162">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="596b5-163">**UsageLocation** — лишь одно из многих свойств, связанных с учетной записью пользователя.</span><span class="sxs-lookup"><span data-stu-id="596b5-163">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="596b5-164">Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **SELECT** и подстановочный знак (\*), чтобы отображать их все для конкретной учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="596b5-164">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="596b5-165">Пример:</span><span class="sxs-lookup"><span data-stu-id="596b5-165">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="596b5-p113">Например, **City** для этого списка — имя свойства, принадлежащего учетной записи пользователя. Это значит, что перечислить все учетные записи пользователей, проживающих в Лондоне, можно с помощью такой команды:</span><span class="sxs-lookup"><span data-stu-id="596b5-p113">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="596b5-168">В приведенных ниже примерах используется синтаксис для командлета **WHERE** **{$ \_ .**</span><span class="sxs-lookup"><span data-stu-id="596b5-168">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="596b5-169">[имя свойства учетной записи пользователя] [оператор сравнения] оно **}**.</span><span class="sxs-lookup"><span data-stu-id="596b5-169">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="596b5-170">[оператор сравнения] имеет значение **-EQ** для Equals, **-Ne** для Not Equals, **-lt** для "больше чем", " **-gt** " для "больше чем", и других.</span><span class="sxs-lookup"><span data-stu-id="596b5-170">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="596b5-171">[Value] как правило, это строка (последовательность букв, цифр и других знаков), числовое значение или **$null** не указано.</span><span class="sxs-lookup"><span data-stu-id="596b5-171">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="596b5-172">Дополнительные [сведения см.](https://technet.microsoft.com/library/hh849715.aspx)</span><span class="sxs-lookup"><span data-stu-id="596b5-172">See [Where](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="596b5-173">Вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="596b5-173">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="596b5-174">Просмотр дополнительных значений свойств для учетных записей</span><span class="sxs-lookup"><span data-stu-id="596b5-174">View additional property values for accounts</span></span>

<span data-ttu-id="596b5-175">Командлет **Get – MsolUser** по умолчанию отображает три свойства учетных записей пользователей:</span><span class="sxs-lookup"><span data-stu-id="596b5-175">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="596b5-176">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="596b5-176">UserPrincipalName</span></span>
    
- <span data-ttu-id="596b5-177">DisplayName</span><span class="sxs-lookup"><span data-stu-id="596b5-177">DisplayName</span></span>
    
- <span data-ttu-id="596b5-178">isLicensed</span><span class="sxs-lookup"><span data-stu-id="596b5-178">isLicensed</span></span>
    
<span data-ttu-id="596b5-179">Если требуются дополнительные свойства, такие как отдел, с которым работает пользователь, и страна или регион, где пользователь использует службы Microsoft 365, можно выполнить командлет **Get-MsolUser** в сочетании с командлетом **SELECT** , чтобы указать список свойств учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="596b5-179">If you need additional properties, such as the department the user works for and the country/region where the user uses Microsoft 365 services, you can run **Get-MsolUser** in combination with the **Select** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="596b5-180">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="596b5-180">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="596b5-181">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="596b5-181">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="596b5-182">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="596b5-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="596b5-183">Отображение только имени, отдела и места использования учетной записи пользователя ( **выберите DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-183">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="596b5-184">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="596b5-184">You should see information similar to this:</span></span>
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="596b5-185">Командлет **SELECT** позволяет выбрать свойства, которые должна отображать команда.</span><span class="sxs-lookup"><span data-stu-id="596b5-185">The **Select** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="596b5-186">Чтобы просмотреть все свойства учетных записей пользователей, используйте подстановочный знак (\*), чтобы отображать их все для конкретной учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="596b5-186">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="596b5-187">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="596b5-187">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="596b5-188">Чтобы сделать более избирательным список учетных записей для отображения, можно также использовать командлет **WHERE** .</span><span class="sxs-lookup"><span data-stu-id="596b5-188">To be more selective about the list of accounts to display, you can also use the **Where** cmdlet.</span></span> <span data-ttu-id="596b5-189">Ниже приведен пример команды, которая выводит только учетные записи, для которых не указано место использования:</span><span class="sxs-lookup"><span data-stu-id="596b5-189">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="596b5-190">Эта команда предписывает PowerShell выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="596b5-190">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="596b5-191">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="596b5-191">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="596b5-192">Найдите все учетные записи пользователей с незаданной областью использования ( **где {$ \_ . UsageLocation-EQ $Null}** ) и отправьте полученные сведения в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-192">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="596b5-193">В фигурных скобках команда задает PowerShell только для поиска набора учетных записей, в которых свойство учетной записи пользователя UsageLocation ( \*\* $ \_ . UsageLocation\*\* ) не указан ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-193">Inside the braces, the command is instructing PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="596b5-194">Отображение только имени, отдела и места использования учетной записи пользователя ( **выберите DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="596b5-194">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="596b5-195">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="596b5-195">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="596b5-196">Если вы используете синхронизацию службы каталогов для создания пользователей Microsoft 365 и управления ими, вы можете отобразить локальную учетную запись, из которой проецируется пользователь Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="596b5-196">If you are using directory synchronization to create and manage your Microsoft 365 users, you can display which local account a Microsoft 365 user has been projected from.</span></span> <span data-ttu-id="596b5-197">В следующем примере предполагается, что служба Azure AD Connect настроена на использование привязки источника по умолчанию ObjectGUID (Дополнительные сведения о настройке привязки источника см. в статье [Azure AD Connect: концепция дизайна](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) и предполагается, что установлен модуль доменных служб Active Directory для PowerShell (см. [инструменты RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="596b5-197">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory Domain Services module for PowerShell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a><span data-ttu-id="596b5-198">См. также</span><span class="sxs-lookup"><span data-stu-id="596b5-198">See also</span></span>

[<span data-ttu-id="596b5-199">Управление учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="596b5-199">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="596b5-200">Управление Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="596b5-200">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="596b5-201">Начало работы с PowerShell для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="596b5-201">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

