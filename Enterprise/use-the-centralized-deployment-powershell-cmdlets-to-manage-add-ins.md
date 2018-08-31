---
title: Управление надстройками с помощью командлетов PowerShell централизованного развертывания
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Использование командлетов PowerShell централизованного развертывания для развертывания и управление надстройками Office для вашей организации Office 365.
ms.openlocfilehash: 6199ad2d37a11166155b898b52d52304836599d0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542550"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="3f105-103">Управление надстройками с помощью командлетов PowerShell централизованного развертывания</span><span class="sxs-lookup"><span data-stu-id="3f105-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="3f105-p101">Как администратор Office 365 надстроек Office можно развернуть для пользователей с помощью централизованного развертывания (см [надстроек развертывания Office в центре администрирования Office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). В дополнение к развертыванию надстроек Office с помощью центра администрирования Office 365, можно также использовать Microsoft PowerShell. [Загрузите](https://go.microsoft.com/fwlink/p/?linkid=850850) командлеты PowerShell централизованного развертывания из центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="3f105-p101">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell. [Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="3f105-107">Подключиться, используя свои учетные данные администратора</span><span class="sxs-lookup"><span data-stu-id="3f105-107">Connect using your admin credentials</span></span>

<span data-ttu-id="3f105-108">Прежде чем использовать командлеты централизованного развертывания, необходимо выполнить вход.</span><span class="sxs-lookup"><span data-stu-id="3f105-108">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="3f105-109">Запустите PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f105-109">Start PowerShell.</span></span>
    
2. <span data-ttu-id="3f105-p102">Подключение к PowerShell с помощью свои учетные данные администратора компании. Выполните следующий командлет.</span><span class="sxs-lookup"><span data-stu-id="3f105-p102">Connect to PowerShell by using your company admin credentials. Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="3f105-p103">На странице **Ввода учетных данных** введите учетные данные глобального администратора Office 365. Кроме того можно ввести учетные данные непосредственно в командлет.</span><span class="sxs-lookup"><span data-stu-id="3f105-p103">In the **Enter Credentials** page, enter your Office 365 global admin credentials. Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="3f105-114">Выполните следующий командлет, определяющее вашей компании учетные данные администратора как объект PSCredential.</span><span class="sxs-lookup"><span data-stu-id="3f105-114">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="3f105-115">Дополнительные сведения об использовании PowerShell можно [подключиться к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="3f105-115">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="3f105-116">Отправка файла манифеста надстройки</span><span class="sxs-lookup"><span data-stu-id="3f105-116">Upload an add-in manifest</span></span>

<span data-ttu-id="3f105-p104">Выполните командлет New-OrganizationAdd-в Отправка файла манифеста надстройки из пути, который может быть расположение файла или URL-адрес. В следующем примере показано расположение файла для значения параметра _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="3f105-p104">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL. The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="3f105-p105">Также можно запустить командлет New-OrganizationAdd-связи для загрузки надстройки и назначения ее к пользователям или группам непосредственно с помощью параметра _члены_ , как показано в следующем примере. Адреса электронной почты членов разделяются точкой с запятой.</span><span class="sxs-lookup"><span data-stu-id="3f105-p105">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example. Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="3f105-121">Загрузка надстройки уровня приложения из магазина Office</span><span class="sxs-lookup"><span data-stu-id="3f105-121">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="3f105-122">Выполните командлет New-OrganizationAddIn для загрузки манифеста из магазина Office.</span><span class="sxs-lookup"><span data-stu-id="3f105-122">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="3f105-123">В следующем примере командлет New-OrganizationAddIn указывает значением код для надстройки для США расположение и содержимое рынка.</span><span class="sxs-lookup"><span data-stu-id="3f105-123">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="3f105-p106">Чтобы определить значение параметра _значением код_ , можно скопировать из URL-адрес в магазин Office веб-страницы для AssetIds надстройки всегда начинаются с «WA», за которым следует номер. Например, в предыдущем примере источник значение значением код WA104099688 — URL-адрес веб-страницы магазина Office для надстройки: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="3f105-p106">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in. AssetIds always begin with "WA" followed by a number. For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="3f105-p107">Значения для параметра _языковой стандарт_ и параметр _ContentMarket_ идентичны и указания страны или региона, вы пытаетесь установить надстройку из. Имеет формат en US, fr-FR. и т. д.</span><span class="sxs-lookup"><span data-stu-id="3f105-p107">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from. The format is en-US, fr-FR. and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="3f105-130">Надстройки, загруженные из магазина Office будет обновляться автоматически в течение нескольких дней Последние обновления, доступные в магазине Office.</span><span class="sxs-lookup"><span data-stu-id="3f105-130">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="3f105-131">Подробные сведения о надстройки</span><span class="sxs-lookup"><span data-stu-id="3f105-131">Get details of an add-in</span></span>

<span data-ttu-id="3f105-132">Выполните командлет Get-OrganizationAddIn, как показано ниже для получения сведений о всех надстройках загружаться в клиент включенные надстройки ИД продукта.</span><span class="sxs-lookup"><span data-stu-id="3f105-132">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="3f105-133">Выполните командлет Get-OrganizationAddIn значение для параметра _ProductId_ , определение которого надстройки, которую необходимо получить подробные сведения по.</span><span class="sxs-lookup"><span data-stu-id="3f105-133">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="3f105-134">Чтобы получить полные сведения о всех надстроек, а также для пользователей и групп, выходные данные командлета Get-OrganizationAddIn в командлет Format-List, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3f105-134">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="3f105-135">Включить или отключить надстройку</span><span class="sxs-lookup"><span data-stu-id="3f105-135">Turn on or turn off an add-in</span></span>

<span data-ttu-id="3f105-136">Чтобы отключить надстройку, пользователи и группы, назначенных на него больше не будет предоставляться доступ, выполните командлет Set-OrganizationAddIn с помощью параметра _ProductId_ и задайте параметра _Enabled_ `$false`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3f105-136">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="3f105-137">Чтобы включить надстройку, выполните командлет же с помощью параметра _Enabled_ , задайте значение `$true`.</span><span class="sxs-lookup"><span data-stu-id="3f105-137">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="3f105-138">Добавление и удаление пользователей из надстройки</span><span class="sxs-lookup"><span data-stu-id="3f105-138">Add or remove users from an add-in</span></span>

<span data-ttu-id="3f105-p108">Добавление пользователей и групп для конкретных надстройки, выполните командлет Set-OrganizationAddInAssignments вместе с параметрами _ProductId_, _Добавить_, а также _элементы_ . Адреса электронной почты членов разделяются точкой с запятой.</span><span class="sxs-lookup"><span data-stu-id="3f105-p108">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters. Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="3f105-141">Чтобы удалить пользователей и групп, выполните командлет же с помощью параметра _удаления_ .</span><span class="sxs-lookup"><span data-stu-id="3f105-141">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="3f105-142">Чтобы назначить надстройки всем пользователям, включенным клиента, выполните командлет же с помощью параметра _AssignToEveryone_ со значением, равным `$true`.</span><span class="sxs-lookup"><span data-stu-id="3f105-142">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="3f105-143">Не назначить надстройки для всеобщего доступа и вернуться к ранее для пользователей и групп, можно запустить командлет же и отключите параметр _AssignToEveryone_ , значение `$false`.</span><span class="sxs-lookup"><span data-stu-id="3f105-143">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="3f105-144">Обновление надстроек</span><span class="sxs-lookup"><span data-stu-id="3f105-144">Update an add-in</span></span>

<span data-ttu-id="3f105-145">Для обновления надстройки уровня приложения из манифеста, выполните командлет Set-OrganizationAddIn с _ProductId_, _ManifestPath_и параметры _языкового стандарта_ , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3f105-145">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="3f105-146">Надстройки, загруженные из магазина Office будет обновляться автоматически в течение нескольких дней Последние обновления, доступные в магазине Office.</span><span class="sxs-lookup"><span data-stu-id="3f105-146">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="3f105-147">Удаление надстройки</span><span class="sxs-lookup"><span data-stu-id="3f105-147">Delete an add-in</span></span>

<span data-ttu-id="3f105-148">Чтобы удалить надстройку, выполните командлет Remove-OrganizationAddIn с параметром _ProductId_ , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3f105-148">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="3f105-149">Получите подробные справки для каждого командлета</span><span class="sxs-lookup"><span data-stu-id="3f105-149">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="3f105-p109">Подробные справки для каждого командлета можно просмотреть с помощью командлета Get-help. Например следующий командлет предоставляет подробные сведения о командлет Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="3f105-p109">You can look at detailed help for each cmdlet by using the Get-help cmdlet. For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


