---
title: "Просмотр учетных записей пользователей с помощью PowerShell для Office 365"
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "Обзор: Просмотр, список или отображение учетные записи пользователей с Office 365 PowerShell разными способами."
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f30a6-103">Просмотр учетных записей пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="f30a6-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="f30a6-104">**Сводка:** Просмотр, список или отображение учетные записи пользователей с Office 365 PowerShell разными способами.</span><span class="sxs-lookup"><span data-stu-id="f30a6-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="f30a6-105">Несмотря на то, что центр администрирования Office 365 можно использовать для просмотра учетных записей для клиента Office 365, можно с помощью Office 365 PowerShell и выполнить некоторые действия, которые невозможно Центр администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="f30a6-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="f30a6-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="f30a6-106">Before you begin</span></span>

<span data-ttu-id="f30a6-p101">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f30a6-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="f30a6-109">Отображение сведений об учетных записях пользователей Office 365</span><span class="sxs-lookup"><span data-stu-id="f30a6-109">Display Office 365 user account information</span></span>

<span data-ttu-id="f30a6-110">Чтобы просмотреть полный список учетных записей пользователей, выполните следующую команду в командной строки на Office 365 PowerShell или PowerShell интегрированная скрипт среды (ISE).</span><span class="sxs-lookup"><span data-stu-id="f30a6-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="f30a6-111">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f30a6-111">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="f30a6-p102">Командлет **Get-MsolUser** также имеет ряд параметров для фильтрации набора отображаются учетные записи пользователей. Например для списка нелицензированных пользователей (пользователей, которые были добавлены в Office 365, но еще не были лицензии на использование любой из служб), выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="f30a6-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="f30a6-114">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f30a6-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="f30a6-115">Дополнительные сведения о дополнительных параметров для фильтрации на отображение набор учетных записей пользователей отображается, можно [Такую](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span><span class="sxs-lookup"><span data-stu-id="f30a6-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="f30a6-p103">Чтобы быть более Выборочный о список учетных записей для отображения, вы можно использовать командлет **Where-Object** в сочетании с помощью командлета **Get-MsolUser** . Чтобы объединить два командлеты, мы используем символ «вертикальная черта» «|», который сообщает Office 365 PowerShell результаты одной команды и отправьте его в следующей команде. Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="f30a6-119">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="f30a6-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f30a6-120">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="f30a6-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f30a6-p104">Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ). В фигурных скобках, команда указывает, что Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( ** $ \_. UsageLocation** ), не является указанного ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="f30a6-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="f30a6-123">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f30a6-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="f30a6-p105">Свойство **UsageLocation** — только один из многих свойства, связанные с учетной записью пользователя. Чтобы просмотреть все свойства для учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (\*) для отображения их все для учетной записи пользователя. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="f30a6-p106">Например в этом списке **Город** — это имя свойства учетной записи пользователя. Это означает, что для получения списка всех учетных записей пользователей для пользователей в Лондон можно использовать следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="f30a6-p107">Синтаксис командлет **Where-Object** , показано в следующих примерах **Where-Object {$\_.** [имя свойства учетной записи пользователя] [оператор сравнения] [значение] **}**. > [оператор сравнения] — это **-eq** значение, **-ne** для не равно, **-lt** меньше, чем **-gt** для больше, чем и другие пользователи > [значение] — это строка (последовательность букв, цифр и других знаков), числовое значение или **$Null** для не определена > [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) более подробные сведения.</span><span class="sxs-lookup"><span data-stu-id="f30a6-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="f30a6-131">Можно проверить состояние блокировки учетной записи пользователя, с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="f30a6-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="f30a6-132">Выбор отображаемых свойств учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="f30a6-132">Select the user account properties to display</span></span>

<span data-ttu-id="f30a6-133">Командлет [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) по умолчанию отображает три свойства учетных записей пользователей:</span><span class="sxs-lookup"><span data-stu-id="f30a6-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="f30a6-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="f30a6-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="f30a6-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f30a6-135">DisplayName</span></span>
    
- <span data-ttu-id="f30a6-136">isLicensed</span><span class="sxs-lookup"><span data-stu-id="f30a6-136">isLicensed</span></span>
    
<span data-ttu-id="f30a6-p108">При необходимости в дополнительных свойств, например отдела, для работы пользователя и страны или региона, где пользователь использует службы Office 365, можно запустить **Такую** в сочетании с командлет **Select-Object** , чтобы указать список учетной записи пользователя свойства. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="f30a6-139">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="f30a6-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f30a6-140">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="f30a6-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f30a6-141">Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="f30a6-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="f30a6-142">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f30a6-142">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

<span data-ttu-id="f30a6-p109">Командлет **Select-Object** позволяет выбрать команду, чтобы отобразить свойства. Чтобы просмотреть все свойства для учетных записей пользователей, используйте подстановочный знак (\*) для отображения их все для учетной записи пользователя. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="f30a6-p110">Чтобы быть более Выборочный о список учетных записей для отображения, вы можно также использовать командлет **Where-Object** . Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="f30a6-148">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="f30a6-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f30a6-149">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="f30a6-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f30a6-p111">Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ) и отправлять полученные сведения к следующей команде ( **|** ). В фигурных скобках, команда рекомендует Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( ** $ \_. UsageLocation** ), не является указанного ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="f30a6-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="f30a6-152">Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="f30a6-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="f30a6-153">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f30a6-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="f30a6-154">Отображение учетных записей пользователей с помощью модуля PowerShell для Azure Active Directory 2</span><span class="sxs-lookup"><span data-stu-id="f30a6-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="f30a6-p112">Чтобы отобразить свойства для учетных записей пользователей с помощью модуля Azure Active Directory версии 2 PowerShell, командлет [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Но для начала необходимо подключиться к своей подписке. Инструкции в разделе[подключение с помощью модуля Azure Active Directory версии 2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="f30a6-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="f30a6-158">Отображение сведений об учетных записях пользователей Office 365</span><span class="sxs-lookup"><span data-stu-id="f30a6-158">Display Office 365 user account information</span></span>

<span data-ttu-id="f30a6-159">Чтобы просмотреть полный список учетных записей пользователей, выполните следующую команду в командной строки на Office 365 PowerShell или PowerShell интегрированная скрипт среды (ISE).</span><span class="sxs-lookup"><span data-stu-id="f30a6-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="f30a6-160">Командлет **Get-AzureADUser** по умолчанию отображает три свойства учетных записей пользователей:</span><span class="sxs-lookup"><span data-stu-id="f30a6-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="f30a6-161">ObjectID</span><span class="sxs-lookup"><span data-stu-id="f30a6-161">ObjectID</span></span>
    
- <span data-ttu-id="f30a6-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f30a6-162">DisplayName</span></span>
    
- <span data-ttu-id="f30a6-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="f30a6-163">UserPrincipalName</span></span>
    
<span data-ttu-id="f30a6-p113">Чтобы быть более Выборочный о список учетных записей для отображения, вы можно использовать командлет **Where-Object** в сочетании с помощью командлета **Get-AzureADUser** . Чтобы объединить два командлеты, мы используем символ «вертикальная черта» «|», который сообщает Office 365 PowerShell результаты одной команды и отправьте его в следующей команде. Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="f30a6-167">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="f30a6-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f30a6-168">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="f30a6-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f30a6-p114">Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ). В фигурных скобках, команда указывает, что Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( ** $ \_. UsageLocation** ), не является указанного ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="f30a6-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="f30a6-p115">Свойство **UsageLocation** — только один из многих свойства, связанные с учетной записью пользователя. Чтобы просмотреть все свойства для учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (\*) для отображения их все для учетной записи пользователя, одну страницу за раз (или **более** ). Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="f30a6-p116">Например **Город** — это имя свойства учетной записи пользователя. Это означает, что для получения списка всех учетных записей пользователей для пользователей в Лондон можно использовать следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="f30a6-p117">Синтаксис командлет **Where-Object** , показано в следующих примерах **Where-Object {$\_.** [имя свойства учетной записи пользователя] [оператор сравнения] [значение] **}**. > [оператор сравнения] — это **-eq** значение, **-ne** для не равно, **-lt** меньше, чем **-gt** для больше, чем и другие пользователи > [значение] — это строка (последовательность букв, цифр и других знаков), числовое значение или **$Null** для не определена >[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) более подробные сведения.</span><span class="sxs-lookup"><span data-stu-id="f30a6-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="f30a6-178">Выбор отображаемых свойств учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="f30a6-178">Select the user account properties to display</span></span>

<span data-ttu-id="f30a6-p118">Командлет **Get-AzureADUser** по умолчанию отображает ObjectID, DisplayName и UserPrincipalName свойства учетных записей пользователей. При необходимости в дополнительных свойств, например отдела, для работы пользователя и страны или региона, где пользователь использует службы Office 365, можно запустить **Get-AzureADUser** в сочетании с командлет **Select-Object** , чтобы указать список пользователей Свойства учетной записи. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="f30a6-182">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="f30a6-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f30a6-183">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="f30a6-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f30a6-184">Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="f30a6-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="f30a6-p119">Чтобы быть более Выборочный о список учетных записей для отображения, вы можно также использовать командлет **Where-Object** . Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:</span><span class="sxs-lookup"><span data-stu-id="f30a6-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="f30a6-187">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="f30a6-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f30a6-188">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="f30a6-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f30a6-p120">Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ) и отправлять полученные сведения к следующей команде ( **|** ). В фигурных скобках, команда рекомендует Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( ** $ \_. UsageLocation** ), не является указанного ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="f30a6-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="f30a6-191">Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="f30a6-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="f30a6-192">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="f30a6-192">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a><span data-ttu-id="f30a6-193">См. также</span><span class="sxs-lookup"><span data-stu-id="f30a6-193">See also</span></span>

#### 

[<span data-ttu-id="f30a6-194">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f30a6-194">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f30a6-195">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="f30a6-195">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f30a6-196">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f30a6-196">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

