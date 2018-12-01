---
title: Просмотр учетных записей пользователей с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
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
description: 'Обзор: Просмотр, список или отображение учетные записи пользователей с Office 365 PowerShell разными способами.'
ms.openlocfilehash: f2743197456cc56f654e99e682108230420384c9
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123256"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="b7dc8-103">Просмотр учетных записей пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="b7dc8-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="b7dc8-104">**Сводка:** Просмотрите учетные записи пользователей с Office 365 PowerShell разными способами.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="b7dc8-105">Несмотря на то, что центр администрирования Office 365 можно использовать для просмотра учетных записей для клиента Office 365, можно с помощью Office 365 PowerShell и выполнить некоторые действия, которые невозможно Центр администрирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="b7dc8-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="b7dc8-106">Before you begin</span></span>

<span data-ttu-id="b7dc8-p101">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information-with-azure-active-directory-powershell-for-graph"></a><span data-ttu-id="b7dc8-109">Отображение сведений учетной записи пользователя Office 365 с помощью Windows Azure Active Directory PowerShell для диаграммы</span><span class="sxs-lookup"><span data-stu-id="b7dc8-109">Display Office 365 user account information with Azure Active Directory PowerShell for Graph</span></span> 

<span data-ttu-id="b7dc8-110">В следующих разделах описано для отображения сведений об учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-110">The following sections describe how to display user account information.</span></span>

### <a name="all-accounts"></a><span data-ttu-id="b7dc8-111">Все учетные записи</span><span class="sxs-lookup"><span data-stu-id="b7dc8-111">All accounts</span></span>

<span data-ttu-id="b7dc8-112">Чтобы просмотреть полный список учетных записей пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-112">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="b7dc8-113">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-113">You should see information similar to this:</span></span>
  
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

### <a name="a-specific-account"></a><span data-ttu-id="b7dc8-114">Конкретной учетной записи</span><span class="sxs-lookup"><span data-stu-id="b7dc8-114">A specific account</span></span>

<span data-ttu-id="b7dc8-115">Чтобы отобразить учетной записи пользователя, заполните поля в имя участника пользователя (UPN) учетной записи пользователя, удалите «<» и «>» символов и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-115">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="additional-property-values-for-a-specific-account"></a><span data-ttu-id="b7dc8-116">Значения дополнительных свойств для конкретной учетной записи</span><span class="sxs-lookup"><span data-stu-id="b7dc8-116">Additional property values for a specific account</span></span>

<span data-ttu-id="b7dc8-117">По умолчанию командлет **Get-AzureADUser** отображается только ObjectID, DisplayName и UserPrincipalName свойств учетных записей.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-117">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="b7dc8-p102">Чтобы быть более Выборочный о список свойств для отображения, вы можно использовать командлет **Select-Object** в сочетании с помощью командлета **Get-AzureADUser** . Чтобы объединить два командлеты, мы используем символ «вертикальная черта» «|», который сообщает Windows Azure Active Directory PowerShell для диаграммы принимают результаты одной команды и отправьте его в следующей команде. Ниже приведен пример команды, которая отображает DisplayName, отдела и UsageLocation для каждой учетной записи пользователя:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p102">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="b7dc8-121">Эта команда дает инструкцию PowerShell для Office 365:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-121">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b7dc8-122">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-122">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b7dc8-123">Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-123">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="b7dc8-p103">Чтобы просмотреть все свойства для учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (\*) для отображения их все для учетной записи пользователя. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p103">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="b7dc8-126">Например можно проверить включенное состояние учетной записи пользователя с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-126">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="some-accounts-based-on-a-common-property"></a><span data-ttu-id="b7dc8-127">Некоторые учетные записи на основе общие свойства</span><span class="sxs-lookup"><span data-stu-id="b7dc8-127">Some accounts based on a common property</span></span>

<span data-ttu-id="b7dc8-p104">Чтобы быть более Выборочный о список учетных записей для отображения, вы можно использовать командлет **Where-Object** в сочетании с помощью командлета **Get-AzureADUser** . Чтобы объединить два командлеты, мы используем символ «вертикальная черта» «|», который сообщает Windows Azure Active Directory PowerShell для диаграммы принимают результаты одной команды и отправьте его в следующей команде. Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p104">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b7dc8-131">Эта команда указывает Windows Azure Active Directory PowerShell для диаграммы:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-131">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="b7dc8-132">Получить всю информацию об учетных записях пользователей (**Get-AzureADUser**) и отправить их следующей команде (**|**).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-132">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b7dc8-p105">Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ). В фигурных скобках, команда указывает, что Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( \*\* $ \_. UsageLocation\*\* ), не является указанного ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p105">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b7dc8-p106">Свойство **UsageLocation** — только один из многих свойства, связанные с учетной записью пользователя. Чтобы просмотреть все свойства для учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (\*) для отображения их все для учетной записи пользователя. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p106">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="b7dc8-p107">Например, **City** для этого списка — имя свойства, принадлежащего учетной записи пользователя. Это значит, что перечислить все учетные записи пользователей, проживающих в Лондоне, можно с помощью такой команды:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p107">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b7dc8-p108">Синтаксис командлет **Where-Object** , показано в следующих примерах **Where-Object {$\_.** [имя свойства учетной записи пользователя] [оператор сравнения] [значение] **}**. > [оператор сравнения] — это **-eq** значение, **-ne** для не равно, **-lt** меньше, чем **-gt** для больше, чем и другим пользователям.  [значение] обычно является строка (последовательность букв, цифр и других знаков), числовое значение или **$Null** для не определена > [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) более подробные сведения.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p108">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="display-office-365-user-account-information-with-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b7dc8-143">Отображение сведений учетной записи пользователя Office 365 с помощью Microsoft Azure модуль Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7dc8-143">Display Office 365 user account information with Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b7dc8-144">В следующих разделах описано для отображения сведений об учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-144">The following sections describe how to display user account information.</span></span>

### <a name="all-accounts"></a><span data-ttu-id="b7dc8-145">Все учетные записи</span><span class="sxs-lookup"><span data-stu-id="b7dc8-145">All accounts</span></span>

<span data-ttu-id="b7dc8-146">Чтобы просмотреть полный список учетных записей пользователей, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-146">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="b7dc8-147">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-147">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="b7dc8-p109">Командлет **Get-MsolUser** также имеет ряд параметров для фильтрации набора отображаются учетные записи пользователей. Например для списка нелицензированных пользователей (пользователей, которые были добавлены в Office 365, но еще не были лицензии на использование любой из служб), выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p109">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="b7dc8-150">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-150">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b7dc8-151">Дополнительные сведения о дополнительных параметров для фильтрации на отображение набор учетных записей пользователей отображается, можно [Такую](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-151">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="a-specific-account"></a><span data-ttu-id="b7dc8-152">Конкретной учетной записи</span><span class="sxs-lookup"><span data-stu-id="b7dc8-152">A specific account</span></span>

<span data-ttu-id="b7dc8-153">Чтобы отобразить учетной записи пользователя, заполните поля в имя участника пользователя (UPN) учетной записи пользователя, удалите «<» и «>» символов и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-153">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="some-accounts-based-on-a-common-property"></a><span data-ttu-id="b7dc8-154">Некоторые учетные записи на основе общие свойства</span><span class="sxs-lookup"><span data-stu-id="b7dc8-154">Some accounts based on a common property</span></span>

<span data-ttu-id="b7dc8-p110">Чтобы быть более Выборочный о список учетных записей для отображения, вы можно использовать командлет **Where-Object** в сочетании с помощью командлета **Get-MsolUser** . Чтобы объединить два командлеты, мы используем символ «вертикальная черта» «|», который сообщает Office 365 PowerShell результаты одной команды и отправьте его в следующей команде. Ниже приведен пример команды, которая отображает только учетные записи пользователей, имеющие место не указано использования:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p110">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b7dc8-158">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-158">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b7dc8-159">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-159">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b7dc8-p111">Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ). В фигурных скобках, команда указывает, что Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( \*\* $ \_. UsageLocation\*\* ), не является указанного ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b7dc8-162">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-162">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="b7dc8-p112">Свойство **UsageLocation** — только один из многих свойства, связанные с учетной записью пользователя. Чтобы просмотреть все свойства для учетных записей пользователей, используйте командлет **Select-Object** и подстановочный знак (\*) для отображения их все для учетной записи пользователя. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p112">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="b7dc8-p113">Например, **City** для этого списка — имя свойства, принадлежащего учетной записи пользователя. Это значит, что перечислить все учетные записи пользователей, проживающих в Лондоне, можно с помощью такой команды:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p113">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b7dc8-p114">Синтаксис командлет **Where-Object** , показано в следующих примерах **Where-Object {$\_.** [имя свойства учетной записи пользователя] [оператор сравнения] [значение] **}**.  [оператор сравнения] — это **-eq** значение, **-ne** для не равно, **-lt** меньше, чем **-gt** для больше, чем и другим пользователям.  [значение] обычно является строка (последовательность букв, цифр и других знаков), числовое значение или **$Null** для не задано. Для получения дополнительных сведений см [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p114">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="b7dc8-173">Можно проверить состояние блокировки учетной записи пользователя, с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-173">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="additional-property-values-for-accounts"></a><span data-ttu-id="b7dc8-174">Значения дополнительных свойств для учетных записей</span><span class="sxs-lookup"><span data-stu-id="b7dc8-174">Additional property values for accounts</span></span>

<span data-ttu-id="b7dc8-175">Командлет **Get-MsolUser** по умолчанию отображает три свойства учетных записей пользователей:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-175">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="b7dc8-176">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="b7dc8-176">UserPrincipalName</span></span>
    
- <span data-ttu-id="b7dc8-177">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b7dc8-177">DisplayName</span></span>
    
- <span data-ttu-id="b7dc8-178">isLicensed</span><span class="sxs-lookup"><span data-stu-id="b7dc8-178">isLicensed</span></span>
    
<span data-ttu-id="b7dc8-p115">При необходимости в дополнительных свойств, например отдела, для работы пользователя и страны или региона, где пользователь использует службы Office 365, можно запустить **Такую** в сочетании с командлет **Select-Object** , чтобы указать список учетной записи пользователя свойства. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p115">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="b7dc8-181">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b7dc8-182">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b7dc8-183">Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-183">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b7dc8-184">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-184">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="b7dc8-p116">Командлет **Select-Object** позволяет выбрать команду, чтобы отобразить свойства. Чтобы просмотреть все свойства для учетных записей пользователей, используйте подстановочный знак (\*) для отображения их все для учетной записи пользователя. Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p116">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="b7dc8-p117">Чтобы еще точнее отфильтровать список отображаемых учетных записей, можно также использовать командлет **Where-Object**. Ниже приведен пример команды, которая выводит только те учетные записи пользователей, для которых не указано расположение использования.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p117">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="b7dc8-190">Эта команда указывает PowerShell в Office 365 сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-190">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b7dc8-191">Получить всю информацию об учетных записях пользователей (**Get-MsolUser**) и передать их в следующую команду (**|**).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-191">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b7dc8-p118">Найти все учетные записи пользователей, имеющие место не указано использования ( **Where-Object {$\_. UsageLocation - eq $Null}** ) и отправлять полученные сведения к следующей команде ( **|** ). В фигурных скобках, команда рекомендует Office 365 PowerShell только поиск набор учетных записей, в которых UsageLocation учетной записью пользователя, свойство ( \*\* $ \_. UsageLocation\*\* ), не является указанного ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p118">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="b7dc8-194">Только пользователь учетная запись имени, отдела и об использовании место отображения ( **DisplayName Select-Object, отдел, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-194">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b7dc8-195">Выходные данные должны выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-195">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="b7dc8-p119">При использовании синхронизации каталогов для создания и управления пользователями Office 365 вы можете отобразить какие локальная учетная запись пользователя с Office 365 были предполагаемое из. В следующем примере предполагается, что подключение Azure AD был настроен на использование привязки источника по умолчанию из ObjectGUID (Дополнительные сведения о настройке привязки источника [Azure AD Connect: Разработка концепции](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)), а также предполагается, что модуль Active Directory для powershell имеет были установленных (см [средства RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="b7dc8-p119">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="new-to-office-365"></a><span data-ttu-id="b7dc8-198">Никогда не работали с Office 365?</span><span class="sxs-lookup"><span data-stu-id="b7dc8-198">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a><span data-ttu-id="b7dc8-199">См. также</span><span class="sxs-lookup"><span data-stu-id="b7dc8-199">See also</span></span>

[<span data-ttu-id="b7dc8-200">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7dc8-200">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b7dc8-201">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="b7dc8-201">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b7dc8-202">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7dc8-202">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

