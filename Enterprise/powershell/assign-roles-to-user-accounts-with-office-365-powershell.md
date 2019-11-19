---
title: Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/30/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: Сводка. Назначайте роли учетным записям пользователей, используя PowerShell для Office 365.
ms.openlocfilehash: 29c23e88d9b7bc2fc0030d467336e38ed413a4ab
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707036"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c290d-103">Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="c290d-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c290d-104">Вы можете быстро и легко назначать роли учетным записям пользователей с помощью PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="c290d-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c290d-105">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="c290d-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c290d-106">Сначала [подключитесь к клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) с помощью учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c290d-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="c290d-p101">Затем определите имя входа для учетной записи пользователя, которую нужно добавить в роль (пример: fredsm@contoso.com). Оно также называется именем участника-пользователя (UPN).</span><span class="sxs-lookup"><span data-stu-id="c290d-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="c290d-109">После этого определите имя роли.</span><span class="sxs-lookup"><span data-stu-id="c290d-109">Next, determine the name of the role.</span></span> <span data-ttu-id="c290d-110">Используйте [список разрешений роли администратора в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="c290d-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="c290d-111">Обратите внимание на примечания в этой статье.</span><span class="sxs-lookup"><span data-stu-id="c290d-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="c290d-112">Некоторые имена ролей отличаются для Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c290d-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="c290d-113">Например роль "Администратор SharePoint" в центре администрирования Microsoft 365 называется "Администратор службы SharePoint" для Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c290d-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="c290d-114">Затем укажите имена для входа и роли и выполните указанные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="c290d-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="c290d-115">Вот пример полного набора команд:</span><span class="sxs-lookup"><span data-stu-id="c290d-115">Here is an example of a completed command set:</span></span>
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="c290d-116">Чтобы отобразить список имен пользователей для определенной роли, используйте указанные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="c290d-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c290d-117">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c290d-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c290d-118">Сначала [подключитесь к клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) с помощью учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="c290d-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="c290d-119">Изменение одной роли</span><span class="sxs-lookup"><span data-stu-id="c290d-119">For a single role change</span></span>

<span data-ttu-id="c290d-120">Наиболее распространенные способы конкретной учетной записи пользователя с отображаемым именем или его адресом электронной почты, также известным именем участника-пользователя (UPN).</span><span class="sxs-lookup"><span data-stu-id="c290d-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="c290d-121">Отображение имен учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="c290d-121">Display names of user accounts</span></span>

<span data-ttu-id="c290d-122">Если вы используете для работы с отображаемыми именами учетных записей пользователей, определите следующее:</span><span class="sxs-lookup"><span data-stu-id="c290d-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="c290d-123">Учетная запись пользователя, которую вы хотите настроить.</span><span class="sxs-lookup"><span data-stu-id="c290d-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="c290d-p104">Чтобы указать учетную запись пользователя, необходимо определить ее отображаемое имя. Чтобы получить список учетных записей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="c290d-p104">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c290d-p105">Эта команда выводит учетные записи пользователей, отсортированное по отображаемому имени, по одному экрану за раз. Вы можете отфильтровать список, используя командлет **Where**. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="c290d-p105">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c290d-129">Эта команда выводит только учетные записи пользователей, отображаемое имя которых начинается со слова "John".</span><span class="sxs-lookup"><span data-stu-id="c290d-129">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="c290d-130">Роль, которую вы хотите назначить.</span><span class="sxs-lookup"><span data-stu-id="c290d-130">The role you want to assign.</span></span>
    
    <span data-ttu-id="c290d-131">Чтобы отобразить список доступных ролей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="c290d-131">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c290d-132">После того как вы определили отображаемое имя учетной записи и имя роли, используйте эти команды, чтобы назначить роль учетной записи:</span><span class="sxs-lookup"><span data-stu-id="c290d-132">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="c290d-p106">Скопируйте команды в Блокнот. Замените описания переменных **$dispName** и **$roleName** их значениями, удалите символы \< и > и оставьте кавычки. Скопируйте измененные строки в окно модуля Windows Azure Active Directory для Windows PowerShell и запустите их. Кроме того, можно использовать интегрированную среду сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c290d-p106">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="c290d-137">Вот пример полного набора команд:</span><span class="sxs-lookup"><span data-stu-id="c290d-137">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="c290d-138">Имена для входа учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="c290d-138">Sign-in names of user accounts</span></span>

<span data-ttu-id="c290d-139">Если вы используете учетные записи или имена участников для учетных записей пользователей, определите следующее:</span><span class="sxs-lookup"><span data-stu-id="c290d-139">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="c290d-140">Имя участника-пользователя для учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="c290d-140">The user account's UPN.</span></span>
    
    <span data-ttu-id="c290d-141">Если вы еще не знаете имя участника-пользователя, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c290d-141">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="c290d-142">Эта команда перечисляет UPN учетных записей пользователей, отсортированных по имени участника-пользователя по одному экрану за раз.</span><span class="sxs-lookup"><span data-stu-id="c290d-142">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="c290d-143">Вы можете отфильтровать список, используя командлет **Where**.</span><span class="sxs-lookup"><span data-stu-id="c290d-143">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="c290d-144">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="c290d-144">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="c290d-145">Эта команда выводит только учетные записи пользователей, отображаемое имя которых начинается со слова "John".</span><span class="sxs-lookup"><span data-stu-id="c290d-145">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="c290d-146">Роль, которую вы хотите назначить.</span><span class="sxs-lookup"><span data-stu-id="c290d-146">The role you want to assign.</span></span>
    
    <span data-ttu-id="c290d-147">Чтобы отобразить список доступных ролей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="c290d-147">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c290d-148">После получения имени участника-пользователя для учетной записи и имени роли выполните следующие команды, чтобы назначить роль учетной записи:</span><span class="sxs-lookup"><span data-stu-id="c290d-148">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="c290d-149">Скопируйте команды в Блокнот.</span><span class="sxs-lookup"><span data-stu-id="c290d-149">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="c290d-150">Для переменных **$upnName** и **$roleName** замените текст описания их значениями, удалите символы \< и > и оставьте кавычки.</span><span class="sxs-lookup"><span data-stu-id="c290d-150">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="c290d-151">Скопируйте измененные строки в окно модуля Windows Azure Active Directory для Windows PowerShell, чтобы запустить их.</span><span class="sxs-lookup"><span data-stu-id="c290d-151">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="c290d-152">Кроме того, вы можете использовать среду Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c290d-152">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="c290d-153">Вот пример полного набора команд:</span><span class="sxs-lookup"><span data-stu-id="c290d-153">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="c290d-154">Изменение нескольких ролей</span><span class="sxs-lookup"><span data-stu-id="c290d-154">For multiple role changes</span></span>

<span data-ttu-id="c290d-155">Определите следующее:</span><span class="sxs-lookup"><span data-stu-id="c290d-155">Determine the following:</span></span>
  
- <span data-ttu-id="c290d-156">Какие учетные записи пользователей вы хотите настроить.</span><span class="sxs-lookup"><span data-stu-id="c290d-156">Which user accounts that you want to configure.</span></span> <span data-ttu-id="c290d-157">Методы, описанные в предыдущем разделе, можно использовать для сбора набора отображаемых имен или UPN.</span><span class="sxs-lookup"><span data-stu-id="c290d-157">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="c290d-158">Какие роли вы хотите назначить каждой учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="c290d-158">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="c290d-159">Чтобы отобразить список доступных ролей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="c290d-159">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c290d-160">Затем создайте текстовый файл с разделителями-запятыми (CSV), в котором отображаются поля отображаемого имени или имени участника-пользователя и имени роли.</span><span class="sxs-lookup"><span data-stu-id="c290d-160">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="c290d-161">Вы можете легко сделать это с помощью Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="c290d-161">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="c290d-162">Ниже приведен пример для отображаемых имен:</span><span class="sxs-lookup"><span data-stu-id="c290d-162">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="c290d-163">Затем укажите расположение CSV-файла и запустите получившиеся команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c290d-163">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="c290d-164">Ниже приведен пример для UPN:</span><span class="sxs-lookup"><span data-stu-id="c290d-164">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="c290d-165">Затем укажите расположение CSV-файла и запустите получившиеся команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c290d-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a><span data-ttu-id="c290d-166">См. также</span><span class="sxs-lookup"><span data-stu-id="c290d-166">See also</span></span>

- [<span data-ttu-id="c290d-167">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c290d-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="c290d-168">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="c290d-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="c290d-169">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c290d-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
