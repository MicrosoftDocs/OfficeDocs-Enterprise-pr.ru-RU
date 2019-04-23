---
title: Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
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
ms.openlocfilehash: 78f2e08df6d46588b93dc217d0e16b7c3a350a88
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957710"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="fc2c6-103">Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="fc2c6-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="fc2c6-104">Вы можете быстро и легко назначать роли учетным записям пользователей с помощью PowerShell для Office 365.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fc2c6-105">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="fc2c6-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="fc2c6-106">Сначала [подключитесь к клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) с помощью учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="fc2c6-p101">Затем определите имя входа для учетной записи пользователя, которую нужно добавить в роль (пример: fredsm@contoso.com). Оно также называется именем участника-пользователя (UPN).</span><span class="sxs-lookup"><span data-stu-id="fc2c6-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="fc2c6-109">После этого определите имя роли.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-109">Next, determine the name of the role.</span></span> <span data-ttu-id="fc2c6-110">Используйте [список разрешений роли администратора в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="fc2c6-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="fc2c6-111">Обратите внимание на примечания в этой статье.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="fc2c6-112">Некоторые имена ролей отличаются для Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="fc2c6-113">Например роль "Администратор SharePoint" в центре администрирования Microsoft 365 называется "Администратор службы SharePoint" для Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="fc2c6-114">Затем укажите имена для входа и роли и выполните указанные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
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

<span data-ttu-id="fc2c6-115">Вот пример полного набора команд:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-115">Here is an example of a completed command set:</span></span>
  
```
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

<span data-ttu-id="fc2c6-116">Чтобы отобразить список имен пользователей для определенной роли, используйте указанные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fc2c6-117">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc2c6-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fc2c6-118">Сначала [подключитесь к клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) с помощью учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="fc2c6-119">Изменение одной роли</span><span class="sxs-lookup"><span data-stu-id="fc2c6-119">For a single role change</span></span>

<span data-ttu-id="fc2c6-120">Определите следующее:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-120">Determine the following:</span></span>
  
- <span data-ttu-id="fc2c6-121">Учетная запись пользователя, которую вы хотите настроить.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-121">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="fc2c6-p104">Чтобы указать учетную запись пользователя, необходимо определить ее отображаемое имя. Чтобы получить список учетных записей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-p104">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="fc2c6-p105">Эта команда выводит учетные записи пользователей, отсортированное по отображаемому имени, по одному экрану за раз. Вы можете отфильтровать список, используя командлет **Where**. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-p105">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="fc2c6-127">Эта команда выводит только учетные записи пользователей, отображаемое имя которых начинается со слова "John".</span><span class="sxs-lookup"><span data-stu-id="fc2c6-127">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="fc2c6-128">Роль, которую вы хотите назначить.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-128">The role you want to assign.</span></span>
    
    <span data-ttu-id="fc2c6-129">Чтобы отобразить список доступных ролей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-129">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="fc2c6-130">После того как вы определили отображаемое имя учетной записи и имя роли, используйте эти команды, чтобы назначить роль учетной записи:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-130">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="fc2c6-p106">Скопируйте команды в Блокнот. Замените описания переменных **$dispName** и **$roleName** их значениями, удалите символы \< и > и оставьте кавычки. Скопируйте измененные строки в окно модуля Windows Azure Active Directory для Windows PowerShell и запустите их. Кроме того, можно использовать интегрированную среду сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-p106">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="fc2c6-135">Вот пример полного набора команд:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-135">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="fc2c6-136">Изменение нескольких ролей</span><span class="sxs-lookup"><span data-stu-id="fc2c6-136">For multiple role changes</span></span>

<span data-ttu-id="fc2c6-137">Определите следующее:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-137">Determine the following:</span></span>
  
- <span data-ttu-id="fc2c6-138">Какие учетные записи пользователей вы хотите настроить.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-138">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="fc2c6-p107">Чтобы указать учетную запись пользователя, необходимо определить ее отображаемое имя. Чтобы получить список учетных записей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-p107">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="fc2c6-p108">Эта команда выводит все учетные записи пользователей, отсортированное по отображаемому имени, по одному экрану за раз. Вы можете отфильтровать список, используя командлет **Where**. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-p108">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="fc2c6-144">Эта команда выводит только учетные записи пользователей, отображаемое имя которых начинается со слова "John".</span><span class="sxs-lookup"><span data-stu-id="fc2c6-144">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="fc2c6-145">Какие роли вы хотите назначить каждой учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-145">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="fc2c6-146">Чтобы отобразить список доступных ролей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-146">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="fc2c6-p109">После этого создайте текстовый CSV-файл, содержащий поля DisplayName и RoleName. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="fc2c6-p109">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="fc2c6-149">Затем укажите расположение CSV-файла и запустите получившиеся команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc2c6-149">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="fc2c6-150">См. также</span><span class="sxs-lookup"><span data-stu-id="fc2c6-150">See also</span></span>

- [<span data-ttu-id="fc2c6-151">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc2c6-151">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="fc2c6-152">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="fc2c6-152">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="fc2c6-153">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc2c6-153">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
