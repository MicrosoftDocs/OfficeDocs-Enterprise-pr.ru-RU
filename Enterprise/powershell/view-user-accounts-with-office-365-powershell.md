---
title: Просмотр учетных записей пользователей с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Сводка: Просмотр, список или отображение учетных записей пользователей различными способами с помощью Office 365 PowerShell.'
ms.openlocfilehash: 10b6d209e76f94b8b001718abd35368f9d1bc29c
ms.sourcegitcommit: ae4b3c1e2859991f3b94690f2eb3b2838d7db2d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2019
ms.locfileid: "30539017"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d1789-103">Просмотр учетных записей пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="d1789-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d1789-104">**Сводка:** Просмотр учетных записей пользователей различными способами с помощью Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1789-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="d1789-105">Несмотря на то, что вы можете использовать центр администрирования Office 365 для просмотра учетных записей клиента Office 365, вы также можете использовать PowerShell для Office 365 и выполнять некоторые действия, которые не могут находиться в центре администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1789-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d1789-106">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="d1789-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d1789-107">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d1789-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="d1789-108">Просмотр всех учетных записей</span><span class="sxs-lookup"><span data-stu-id="d1789-108">View all accounts</span></span>

<span data-ttu-id="d1789-109">Чтобы отобразить полный список учетных записей пользователей, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="d1789-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="d1789-110">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1789-110">You should see information similar to this:</span></span>
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="d1789-111">Просмотр определенной учетной записи</span><span class="sxs-lookup"><span data-stu-id="d1789-111">View a specific account</span></span>

<span data-ttu-id="d1789-112">Чтобы отобразить определенную учетную запись пользователя, введите имя учетной записи пользователя, также называемое именем участника-пользователя (UPN), удалите символы "_Лт_" и "_Гт_", а затем выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="d1789-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="d1789-113">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="d1789-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="d1789-114">Просмотр дополнительных значений свойств для конкретной учетной записи</span><span class="sxs-lookup"><span data-stu-id="d1789-114">View additional property values for a specific account</span></span>

<span data-ttu-id="d1789-115">По умолчанию командлет **Get – AzureADUser** отображает свойства ObjectID, DisplayName и userPrincipalName для учетных записей.</span><span class="sxs-lookup"><span data-stu-id="d1789-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="d1789-116">Чтобы сделать более избирательным список отображаемых свойств, можно использовать командлет **Select – Object** в сочетании с командлетом **Get – AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="d1789-116">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="d1789-117">Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который сообщает PowerShell Active Directory PowerShell для Graph, чтобы получить результаты одной команды и отправить ее следующей команде.</span><span class="sxs-lookup"><span data-stu-id="d1789-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="d1789-118">Ниже приведен пример команды, которая отображает DisplayName, Department и UsageLocation для каждой учетной записи пользователя:</span><span class="sxs-lookup"><span data-stu-id="d1789-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="d1789-119">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="d1789-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1789-120">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="d1789-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1789-121">Отображение только имени, отдела и места использования учетной записи пользователя ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="d1789-122">Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (\*), чтобы отображать их все для конкретной учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="d1789-122">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="d1789-123">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="d1789-123">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="d1789-124">В качестве другого примера можно проверить включенное состояние конкретной учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="d1789-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="d1789-125">Просмотр некоторых учетных записей на основе общего свойства</span><span class="sxs-lookup"><span data-stu-id="d1789-125">View some accounts based on a common property</span></span>

<span data-ttu-id="d1789-126">Чтобы еще точнее отфильтровать список отображаемых учетных записей, можно использовать сочетание командлетов **Where-Object** и **Get-AzureADUser**.</span><span class="sxs-lookup"><span data-stu-id="d1789-126">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="d1789-127">Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который сообщает PowerShell Active Directory PowerShell для Graph, чтобы получить результаты одной команды и отправить ее следующей команде.</span><span class="sxs-lookup"><span data-stu-id="d1789-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="d1789-128">Ниже приведен пример команды, которая выводит только учетные записи, для которых не указано место использования:</span><span class="sxs-lookup"><span data-stu-id="d1789-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="d1789-129">Эта команда указывает Azure Active Directory PowerShell для Graph:</span><span class="sxs-lookup"><span data-stu-id="d1789-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="d1789-130">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="d1789-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1789-131">Найдите все учетные записи пользователей с незаданной областью использования ( **где-Object {$\_. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-131">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="d1789-132">В фигурных скобках команда инструктирует Office 365 PowerShell, чтобы найти только те учетные записи, в которых свойство учетной записи пользователя UsageLocation ( \*\* $ \_. UsageLocation\*\* ) не указан ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-132">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="d1789-133">**UsageLocation** — лишь одно из многих свойств, связанных с учетной записью пользователя.</span><span class="sxs-lookup"><span data-stu-id="d1789-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="d1789-134">Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (\*), чтобы отображать их все для конкретной учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="d1789-134">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="d1789-135">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="d1789-135">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="d1789-p106">Например, **City** для этого списка — имя свойства, принадлежащего учетной записи пользователя. Это значит, что перечислить все учетные записи пользователей, проживающих в Лондоне, можно с помощью такой команды:</span><span class="sxs-lookup"><span data-stu-id="d1789-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="d1789-138">Для командлета **Where-Object** , показанного в этих примерах, используется синтаксис **Where-\_Object {$.**</span><span class="sxs-lookup"><span data-stu-id="d1789-138">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="d1789-139">[имя свойства учетной записи пользователя] [оператор сравнения] оно **}**. _гт_ [оператор сравнения] имеет значение **-EQ** для Equals, **-Ne** для Not Equals, **-lt** для "меньше, чем", "-gt" для "больше чем", " **-gt** " и других.</span><span class="sxs-lookup"><span data-stu-id="d1789-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="d1789-140">[Value] как правило, это строка (последовательность букв, цифр и других знаков), числовое значение или **$null** унспеЦифиед_гт_ для получения дополнительных сведений см [](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .</span><span class="sxs-lookup"><span data-stu-id="d1789-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d1789-141">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1789-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d1789-142">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d1789-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="d1789-143">Просмотр всех учетных записей</span><span class="sxs-lookup"><span data-stu-id="d1789-143">View all accounts</span></span>

<span data-ttu-id="d1789-144">Чтобы отобразить полный список учетных записей пользователей, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="d1789-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="d1789-145">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1789-145">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="d1789-146">У командлета **Get-MsolUser** также есть ряд параметров для фильтрации отображаемых учетных данных.</span><span class="sxs-lookup"><span data-stu-id="d1789-146">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="d1789-147">Например, для списка нелицензированных пользователей (пользователей, которые были добавлены в Office 365, но еще не лицензированы для использования каких-либо служб) выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="d1789-147">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="d1789-148">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1789-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="d1789-149">Дополнительные сведения о дополнительных параметрах для фильтрации отображаемого набора учетных записей пользователей приведены в статье [Get – MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="d1789-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="d1789-150">Просмотр определенной учетной записи</span><span class="sxs-lookup"><span data-stu-id="d1789-150">View a specific account</span></span>

<span data-ttu-id="d1789-151">Чтобы отобразить определенную учетную запись пользователя, введите учетную запись пользователя учетной записи пользователя, которая также называется именем участника-пользователя (UPN), удалите символы "_Лт_" и "_Гт_", а затем выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="d1789-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="d1789-152">Просмотр некоторых учетных записей на основе общего свойства</span><span class="sxs-lookup"><span data-stu-id="d1789-152">View some accounts based on a common property</span></span>

<span data-ttu-id="d1789-153">Чтобы еще точнее отфильтровать список отображаемых учетных записей, можно использовать сочетание командлетов **Where-Object** и **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="d1789-153">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="d1789-154">Чтобы объединить два командлета, мы используем символ ' ' pipe ' ' | ", который указывает оболочке PowerShell Office 365 для получения результатов одной команды и отправки их следующей команде.</span><span class="sxs-lookup"><span data-stu-id="d1789-154">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="d1789-155">Ниже приведен пример команды, которая выводит только учетные записи, для которых не указано место использования:</span><span class="sxs-lookup"><span data-stu-id="d1789-155">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="d1789-156">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="d1789-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1789-157">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="d1789-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1789-158">Найдите все учетные записи пользователей с незаданной областью использования ( **где-Object {$\_. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-158">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="d1789-159">В фигурных скобках команда инструктирует Office 365 PowerShell, чтобы найти только те учетные записи, в которых свойство учетной записи пользователя UsageLocation ( \*\* $ \_. UsageLocation\*\* ) не указан ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-159">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="d1789-160">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1789-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="d1789-161">**UsageLocation** — лишь одно из многих свойств, связанных с учетной записью пользователя.</span><span class="sxs-lookup"><span data-stu-id="d1789-161">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="d1789-162">Чтобы просмотреть все свойства учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (\*), чтобы отображать их все для конкретной учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="d1789-162">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="d1789-163">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="d1789-163">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="d1789-p112">Например, **City** для этого списка — имя свойства, принадлежащего учетной записи пользователя. Это значит, что перечислить все учетные записи пользователей, проживающих в Лондоне, можно с помощью такой команды:</span><span class="sxs-lookup"><span data-stu-id="d1789-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="d1789-166">Для командлета **Where-Object** , показанного в этих примерах, используется синтаксис **Where-\_Object {$.**</span><span class="sxs-lookup"><span data-stu-id="d1789-166">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="d1789-167">[имя свойства учетной записи пользователя] [оператор сравнения] оно **}**.</span><span class="sxs-lookup"><span data-stu-id="d1789-167">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="d1789-168">[оператор сравнения] имеет значение **-EQ** для Equals, **-Ne** для Not Equals, **-lt** для "больше чем", " **-gt** " для "больше чем", и других.</span><span class="sxs-lookup"><span data-stu-id="d1789-168">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="d1789-169">[Value] как правило, это строка (последовательность букв, цифр и других знаков), числовое значение или **$null** не указано.</span><span class="sxs-lookup"><span data-stu-id="d1789-169">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="d1789-170">Для [](https://technet.microsoft.com/en-us/library/hh849715.aspx) получения дополнительных сведений см.</span><span class="sxs-lookup"><span data-stu-id="d1789-170">See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="d1789-171">Вы можете проверить состояние блокировки учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="d1789-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="d1789-172">Просмотр дополнительных значений свойств для учетных записей</span><span class="sxs-lookup"><span data-stu-id="d1789-172">View additional property values for accounts</span></span>

<span data-ttu-id="d1789-173">Командлет **Get – MsolUser** по умолчанию отображает три свойства учетных записей пользователей:</span><span class="sxs-lookup"><span data-stu-id="d1789-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="d1789-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="d1789-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="d1789-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d1789-175">DisplayName</span></span>
    
- <span data-ttu-id="d1789-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="d1789-176">isLicensed</span></span>
    
<span data-ttu-id="d1789-177">Если требуются дополнительные свойства, такие как отдел, с которым работает пользователь, и страна или регион, где пользователь использует службы Office 365, можно выполнить командлет **Get-MsolUser** в сочетании с командлетом **Select-Object** , чтобы указать список учетных записей пользователей. параметры.</span><span class="sxs-lookup"><span data-stu-id="d1789-177">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="d1789-178">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="d1789-178">Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="d1789-179">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="d1789-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1789-180">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="d1789-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1789-181">Отображение только имени, отдела и места использования учетной записи пользователя ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="d1789-182">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1789-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="d1789-183">Командлет **Select – Object** позволяет выбирать и выбирать свойства, которые должна отображать команда.</span><span class="sxs-lookup"><span data-stu-id="d1789-183">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="d1789-184">Чтобы просмотреть все свойства учетных записей пользователей, используйте подстановочный знак (\*), чтобы отображать их все для конкретной учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="d1789-184">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="d1789-185">Пример:</span><span class="sxs-lookup"><span data-stu-id="d1789-185">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="d1789-p116">Чтобы еще точнее отфильтровать список отображаемых учетных записей, можно также использовать командлет **Where-Object**. Ниже приведен пример команды, которая выводит только те учетные записи пользователей, для которых не указано расположение использования.</span><span class="sxs-lookup"><span data-stu-id="d1789-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="d1789-188">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="d1789-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1789-189">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="d1789-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1789-190">Найдите все учетные записи пользователей с незаданной областью использования ( **где-Object {$\_. UsageLocation-EQ $Null}** ) и отправьте полученные сведения в следующую команду ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-190">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="d1789-191">В фигурных скобках команда предписывает PowerShell Office 365, чтобы найти только те учетные записи, в которых свойство учетной записи пользователя UsageLocation ( \*\* $ \_. UsageLocation\*\* ) не указан ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-191">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="d1789-192">Отображение только имени, отдела и места использования учетной записи пользователя ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="d1789-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="d1789-193">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1789-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="d1789-194">Если вы используете синхронизацию службы каталогов для создания пользователей Office 365 и управления ими, вы можете отобразить локальную учетную запись, с которой был проецирован пользователь Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1789-194">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="d1789-195">Ниже предполагается, что Azure AD Connect настроен на использование привязки источника по умолчанию ObjectGUID (Дополнительные сведения о настройке привязки источника см. в статье [Azure AD Connect: концепция дизайна](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) и предполагается, что модуль Active Directory для PowerShell установлены (см. [инструменты RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="d1789-195">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="d1789-196">См. также</span><span class="sxs-lookup"><span data-stu-id="d1789-196">See also</span></span>

[<span data-ttu-id="d1789-197">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1789-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d1789-198">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="d1789-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d1789-199">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1789-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

