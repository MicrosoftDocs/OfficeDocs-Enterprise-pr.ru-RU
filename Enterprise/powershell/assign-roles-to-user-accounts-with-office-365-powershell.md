---
title: "Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365"
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
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "Сводка. Используйте PowerShell в Office 365 и командлет Add-MsolRoleMember для назначения ролей учетным записям пользователей."
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f13bb-103">Назначение ролей учетным записям пользователей с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="f13bb-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="f13bb-104">**Сводка.** Назначайте роли учетным записям пользователей, используя PowerShell для Office 365 и командлет **Add-MsolRoleMember**.</span><span class="sxs-lookup"><span data-stu-id="f13bb-104">Summary: Use Office 365 PowerShell and the Add-MsolRoleMember cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="f13bb-105">Вы можете быстро и легко назначать роли с помощью PowerShell для Office 365, указывая отображаемое имя учетной записи пользователя и имя роли.</span><span class="sxs-lookup"><span data-stu-id="f13bb-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's Display Name and the role's Name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="f13bb-106">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="f13bb-106">Before you begin</span></span>

<span data-ttu-id="f13bb-p101">Чтобы выполнять процедуры, описанные в этой статье, необходимо подключиться к PowerShell в Office 365, используя учетную запись глобального администратора. Инструкции см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f13bb-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="f13bb-109">Изменение одной роли</span><span class="sxs-lookup"><span data-stu-id="f13bb-109">For a single role change</span></span>

<span data-ttu-id="f13bb-110">Определите следующее:</span><span class="sxs-lookup"><span data-stu-id="f13bb-110">Determine the following:</span></span>
  
- <span data-ttu-id="f13bb-111">Учетная запись пользователя, которую вы хотите настроить.</span><span class="sxs-lookup"><span data-stu-id="f13bb-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="f13bb-p102">Чтобы указать учетную запись пользователя, необходимо определить ее отображаемое имя. Чтобы получить список учетных записей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="f13bb-p102">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="f13bb-p103">Эта команда выводит учетные записи пользователей, отсортированное по отображаемому имени, по одному экрану за раз. Вы можете отфильтровать список, используя командлет **Where**. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="f13bb-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="f13bb-117">Эта команда выводит только учетные записи пользователей, отображаемое имя которых начинается со слова "John".</span><span class="sxs-lookup"><span data-stu-id="f13bb-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="f13bb-118">Роль, которую вы хотите назначить.</span><span class="sxs-lookup"><span data-stu-id="f13bb-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="f13bb-119">Чтобы отобразить список доступных ролей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="f13bb-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="f13bb-120">После того как вы определили отображаемое имя учетной записи и имя роли, используйте эти команды, чтобы назначить роль учетной записи:</span><span class="sxs-lookup"><span data-stu-id="f13bb-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="f13bb-p104">Скопируйте команды в Блокнот. Замените описания переменных **$dispName** и **$roleName** их значениями, удалите символы \< и > и оставьте кавычки. Скопируйте измененные строки в окно модуля Windows Azure Active Directory для Windows PowerShell и запустите их. Кроме того, можно использовать интегрированную среду сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f13bb-p104">Copy the commands and paste them into Notepad. For the $dispName and $roleName variables, replace the description text with their values, remove the < and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="f13bb-125">Вот пример полного набора команд:</span><span class="sxs-lookup"><span data-stu-id="f13bb-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="f13bb-126">Изменение нескольких ролей</span><span class="sxs-lookup"><span data-stu-id="f13bb-126">For multiple role changes</span></span>

<span data-ttu-id="f13bb-127">Определите следующее:</span><span class="sxs-lookup"><span data-stu-id="f13bb-127">Determine the following:</span></span>
  
- <span data-ttu-id="f13bb-128">Какие учетные записи пользователей вы хотите настроить.</span><span class="sxs-lookup"><span data-stu-id="f13bb-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="f13bb-p105">Чтобы указать учетную запись пользователя, необходимо определить ее отображаемое имя. Чтобы получить список учетных записей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="f13bb-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="f13bb-p106">Эта команда выводит все учетные записи пользователей, отсортированное по отображаемому имени, по одному экрану за раз. Вы можете отфильтровать список, используя командлет **Where**. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="f13bb-p106">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="f13bb-134">Эта команда выводит только учетные записи пользователей, отображаемое имя которых начинается со слова "John".</span><span class="sxs-lookup"><span data-stu-id="f13bb-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="f13bb-135">Какие роли вы хотите назначить каждой учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="f13bb-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="f13bb-136">Чтобы отобразить список доступных ролей, используйте эту команду:</span><span class="sxs-lookup"><span data-stu-id="f13bb-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="f13bb-p107">После этого создайте текстовый CSV-файл, содержащий поля DisplayName и RoleName. Вот пример:</span><span class="sxs-lookup"><span data-stu-id="f13bb-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="f13bb-139">Затем укажите расположение CSV-файла и запустите получившиеся команды в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f13bb-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="f13bb-140">См. также</span><span class="sxs-lookup"><span data-stu-id="f13bb-140">See also</span></span>

#### 

[<span data-ttu-id="f13bb-141">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f13bb-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f13bb-142">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="f13bb-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f13bb-143">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f13bb-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

[<span data-ttu-id="f13bb-144">Add-MsolRoleMember</span><span class="sxs-lookup"><span data-stu-id="f13bb-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)

