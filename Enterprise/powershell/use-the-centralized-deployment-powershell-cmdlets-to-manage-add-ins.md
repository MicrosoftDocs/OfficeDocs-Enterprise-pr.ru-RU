---
title: Использование командлетов PowerShell для централизованного развертывания для управления надстройками
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Используйте командлеты PowerShell централизованного развертывания для развертывания надстроек Office для организации Office 365 и управления ими.
ms.openlocfilehash: 586b66ac3632a5d86a63014a50f3c605b1c005e7
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844160"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="228e0-103">Использование командлетов PowerShell для централизованного развертывания для управления надстройками</span><span class="sxs-lookup"><span data-stu-id="228e0-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="228e0-104">Администраторы Office 365 могут развертывать надстройки Office для пользователей с помощью функции централизованного развертывания (см. [Управление развертыванием надстроек office 365 в центре администрирования](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span><span class="sxs-lookup"><span data-stu-id="228e0-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="228e0-105">Кроме развертывания надстроек Office с помощью центра администрирования, вы также можете использовать Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="228e0-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="228e0-106">[Скачайте](https://go.microsoft.com/fwlink/p/?linkid=850850) командлеты PowerShell для централизованного развертывания из центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="228e0-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="228e0-107">Что нужно сделать</span><span class="sxs-lookup"><span data-stu-id="228e0-107">What do you want to do?</span></span>

[<span data-ttu-id="228e0-108">Подключение с использованием учетных данных администратора</span><span class="sxs-lookup"><span data-stu-id="228e0-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="228e0-109">Отправка манифеста надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="228e0-110">Отправка надстройки из магазина Office</span><span class="sxs-lookup"><span data-stu-id="228e0-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="228e0-111">Получение сведений о надстройке</span><span class="sxs-lookup"><span data-stu-id="228e0-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="228e0-112">Включение и отключение надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="228e0-113">Добавление и удаление пользователей из надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="228e0-114">Обновление надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="228e0-115">Удаление надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="228e0-116">Получение подробной справки для каждого командлета</span><span class="sxs-lookup"><span data-stu-id="228e0-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="228e0-117">Подключение с использованием учетных данных администратора</span><span class="sxs-lookup"><span data-stu-id="228e0-117">Connect using your admin credentials</span></span>
<span data-ttu-id="228e0-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-118"><a name="BKMK_Connect"> </a></span></span>

<span data-ttu-id="228e0-119">Прежде чем использовать командлеты централизованного развертывания, необходимо войти в систему.</span><span class="sxs-lookup"><span data-stu-id="228e0-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="228e0-120">Запустите PowerShell.</span><span class="sxs-lookup"><span data-stu-id="228e0-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="228e0-121">Подключитесь к PowerShell с помощью учетных данных администратора компании.</span><span class="sxs-lookup"><span data-stu-id="228e0-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="228e0-122">Выполните следующий командлет.</span><span class="sxs-lookup"><span data-stu-id="228e0-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="228e0-123">На странице **введите учетные данные** введите учетные данные глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="228e0-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="228e0-124">Кроме того, вы можете ввести свои учетные данные непосредственно в командлет.</span><span class="sxs-lookup"><span data-stu-id="228e0-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="228e0-125">Выполните следующий командлет, указав учетные данные администратора компании в качестве объекта PSCredential.</span><span class="sxs-lookup"><span data-stu-id="228e0-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="228e0-126">Дополнительные сведения об использовании PowerShell приведены в статье [Подключение к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="228e0-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="228e0-127">Отправка манифеста надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-127">Upload an add-in manifest</span></span>
<span data-ttu-id="228e0-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-128"><a name="BKMK_UploadManifest"> </a></span></span>

<span data-ttu-id="228e0-129">Выполните командлет New-Организациянадстройки-in, чтобы отправить манифест надстройки по пути, который может представлять собой расположение файла или URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="228e0-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="228e0-130">В следующем примере показано расположение файла для значения параметра _манифестпас_ .</span><span class="sxs-lookup"><span data-stu-id="228e0-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="228e0-131">Кроме того, можно выполнить командлет New – Организациянадстройки – in, чтобы отправить надстройку и назначить ее пользователям или группам напрямую с помощью параметра _Members_ , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="228e0-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="228e0-132">Разделяйте адреса электронной почты членов запятыми.</span><span class="sxs-lookup"><span data-stu-id="228e0-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="228e0-133">Отправка надстройки из магазина Office</span><span class="sxs-lookup"><span data-stu-id="228e0-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="228e0-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-134"><a name="BKMK_UploadAddin"> </a></span></span>

<span data-ttu-id="228e0-135">Выполните командлет New – Организатионаддин, чтобы отправить манифест из магазина Office.</span><span class="sxs-lookup"><span data-stu-id="228e0-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="228e0-136">В следующем примере командлет New – Организатионаддин указывает Ассетид для надстройки для местонахождения США и рынка контента.</span><span class="sxs-lookup"><span data-stu-id="228e0-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="228e0-137">Чтобы определить значение параметра _ассетид_ , можно скопировать его из URL-адреса веб-страницы магазина Office для надстройки.</span><span class="sxs-lookup"><span data-stu-id="228e0-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="228e0-138">Ассетидс всегда начинается с "WA", за которым следует число.</span><span class="sxs-lookup"><span data-stu-id="228e0-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="228e0-139">Например, в предыдущем примере источник для значения Ассетид для WA104099688 — это URL-адрес веб-страницы магазина Office для надстройки: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="228e0-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="228e0-140">Значения параметра _locale_ и параметра _контентмаркет_ идентичны и указывают страну или регион, из которого вы пытаетесь установить надстройку.</span><span class="sxs-lookup"><span data-stu-id="228e0-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="228e0-141">Формат — en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="228e0-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="228e0-142">и т. д.</span><span class="sxs-lookup"><span data-stu-id="228e0-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="228e0-143">Надстройки, отправленные из магазина Office, автоматически обновляются в течение нескольких дней с последнего обновления, доступного в магазине Office.</span><span class="sxs-lookup"><span data-stu-id="228e0-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="228e0-144">Получение сведений о надстройке</span><span class="sxs-lookup"><span data-stu-id="228e0-144">Get details of an add-in</span></span>
<span data-ttu-id="228e0-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-145"><a name="BKMK_GetDetails"> </a></span></span>

<span data-ttu-id="228e0-146">Выполните командлет Get – Организатионаддин, как показано ниже, чтобы получить сведения обо всех надстройках, отправленных в клиент, включающих идентификатор продукта надстройки.</span><span class="sxs-lookup"><span data-stu-id="228e0-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="228e0-147">Выполните командлет Get – Организатионаддин со значением параметра _ProductID_ , чтобы указать, для какой надстройки необходимо получить сведения.</span><span class="sxs-lookup"><span data-stu-id="228e0-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="228e0-148">Чтобы получить полные сведения обо всех надстройках, а также о назначенных пользователях и группах, перечислите выходные данные командлета Get – Организатионаддин в командлет Format – List, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="228e0-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="228e0-149">Включение и отключение надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="228e0-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-150"><a name="BKMK_TurnOnOff"> </a></span></span>

<span data-ttu-id="228e0-151">Чтобы отключить надстройку, чтобы пользователи и группы, которым назначена эта надстройка, больше не были доступны, выполните командлет Set – Организатионаддин с параметром _ProductID_ и параметром _Enabled_ `$false`, равным, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="228e0-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="228e0-152">Чтобы снова включить надстройку, выполните тот же командлет, для `$true`параметра _Enabled_ которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="228e0-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="228e0-153">Добавление и удаление пользователей из надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="228e0-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-154"><a name="BKMK_AddRemove"> </a></span></span>

<span data-ttu-id="228e0-155">Чтобы добавить пользователей и группы в определенную надстройку, выполните командлет Set – Организатионаддинассигнментс с параметрами _ProductID_, _Add_и _Members_ .</span><span class="sxs-lookup"><span data-stu-id="228e0-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="228e0-156">Разделяйте адреса электронной почты членов запятыми.</span><span class="sxs-lookup"><span data-stu-id="228e0-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="228e0-157">Чтобы удалить пользователей и группы, выполните один командлет с параметром _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="228e0-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="228e0-158">Чтобы назначить надстройку всем пользователям в клиенте, выполните тот же командлет с параметром _ассигнтоеверйоне_ , для `$true`которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="228e0-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="228e0-159">Чтобы не присваивать надстройке всем пользователям и вернуться к ранее назначенным пользователям и группам, можно выполнить один и тот же командлет и отключить параметр _ассигнтоеверйоне_ , присвоив ему значение `$false`.</span><span class="sxs-lookup"><span data-stu-id="228e0-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="228e0-160">Обновление надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-160">Update an add-in</span></span>
<span data-ttu-id="228e0-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-161"><a name="BKMK_UpdateAddin"> </a></span></span>

<span data-ttu-id="228e0-162">Чтобы обновить надстройку с помощью манифеста, выполните командлет Set – Организатионаддин с параметрами _ProductID_, _манифестпас_и _locale_ , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="228e0-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="228e0-163">Надстройки, отправленные из магазина Office, автоматически обновляются в течение нескольких дней с последнего обновления, доступного в магазине Office.</span><span class="sxs-lookup"><span data-stu-id="228e0-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="228e0-164">Удаление надстройки</span><span class="sxs-lookup"><span data-stu-id="228e0-164">Delete an add-in</span></span>
<span data-ttu-id="228e0-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-165"><a name="BKMK_Delete"> </a></span></span>

<span data-ttu-id="228e0-166">Чтобы удалить надстройку, запустите командлет Remove – Организатионаддин с параметром _ProductID_ , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="228e0-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="228e0-167">Получение подробной справки для каждого командлета</span><span class="sxs-lookup"><span data-stu-id="228e0-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="228e0-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="228e0-168"><a name="BKMK_GetHelp"> </a></span></span>

<span data-ttu-id="228e0-169">С помощью командлета Get – Help можно просмотреть подробную справку для каждого командлета.</span><span class="sxs-lookup"><span data-stu-id="228e0-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="228e0-170">Например, следующий командлет предоставляет подробные сведения о командлете Remove – Организатионаддин.</span><span class="sxs-lookup"><span data-stu-id="228e0-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


