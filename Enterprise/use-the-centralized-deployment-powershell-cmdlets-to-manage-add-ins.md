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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Используйте командлеты PowerShell централизованного развертывания для развертывания надстроек Office для организации Office 365 и управления ими.
ms.openlocfilehash: c63a48d212bba4eda25fb6b8843f6321892dc54b
ms.sourcegitcommit: d53033c2d2d41d52047e3e2644d77373d4a5dd9a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "35791254"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="76955-103">Использование командлетов PowerShell для централизованного развертывания для управления надстройками</span><span class="sxs-lookup"><span data-stu-id="76955-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="76955-104">Как глобальный администратор Microsoft 365 или администратор Exchange вы можете развертывать надстройки Office для пользователей с помощью функции централизованного развертывания (см. раздел [Развертывание надстроек Office в центре администрирования](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span><span class="sxs-lookup"><span data-stu-id="76955-104">As a Microsoft 365 global, or Exchange admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="76955-105">Кроме развертывания надстроек Office с помощью центра администрирования Microsoft 365, вы также можете использовать Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76955-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="76955-106">Установите [модуль развертывания Office 365 с централизованной надстройкой для Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span><span class="sxs-lookup"><span data-stu-id="76955-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="76955-107">После загрузки модуля откройте обычное окно Windows PowerShell и запустите следующий командлет:</span><span class="sxs-lookup"><span data-stu-id="76955-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="76955-108">Подключение с использованием учетных данных администратора</span><span class="sxs-lookup"><span data-stu-id="76955-108">Connect using your admin credentials</span></span>

<span data-ttu-id="76955-109">Прежде чем использовать командлеты централизованного развертывания, необходимо войти в систему.</span><span class="sxs-lookup"><span data-stu-id="76955-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="76955-110">Запустите PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76955-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="76955-111">Подключитесь к PowerShell с помощью учетных данных администратора компании.</span><span class="sxs-lookup"><span data-stu-id="76955-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="76955-112">Выполните следующий командлет.</span><span class="sxs-lookup"><span data-stu-id="76955-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="76955-113">На странице **введите учетные данные** введите учетные данные глобального администратора Office 365.</span><span class="sxs-lookup"><span data-stu-id="76955-113">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="76955-114">Кроме того, вы можете ввести свои учетные данные непосредственно в командлет.</span><span class="sxs-lookup"><span data-stu-id="76955-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="76955-115">Выполните следующий командлет, указав учетные данные администратора компании в качестве объекта PSCredential.</span><span class="sxs-lookup"><span data-stu-id="76955-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="76955-116">Дополнительные сведения об использовании PowerShell приведены в статье [Подключение к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="76955-116">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="76955-117">Отправка манифеста надстройки</span><span class="sxs-lookup"><span data-stu-id="76955-117">Upload an add-in manifest</span></span>

<span data-ttu-id="76955-118">Выполните командлет **New-организациянадстройки-in** , чтобы отправить манифест надстройки по пути, который может представлять собой расположение файла или URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="76955-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="76955-119">В следующем примере показано расположение файла для значения параметра _манифестпас_ .</span><span class="sxs-lookup"><span data-stu-id="76955-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="76955-120">Кроме того, можно выполнить командлет **New – организациянадстройки – in** , чтобы отправить надстройку и назначить ее пользователям или группам напрямую с помощью параметра Members __ , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="76955-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="76955-121">Разделяйте адреса электронной почты членов запятыми.</span><span class="sxs-lookup"><span data-stu-id="76955-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="76955-122">Отправка надстройки из магазина Office</span><span class="sxs-lookup"><span data-stu-id="76955-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="76955-123">Выполните командлет **New – организатионаддин** , чтобы отправить манифест из магазина Office.</span><span class="sxs-lookup"><span data-stu-id="76955-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="76955-124">В следующем примере командлет **New – организатионаддин** указывает ассетид для надстройки для местонахождения США и рынка контента.</span><span class="sxs-lookup"><span data-stu-id="76955-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="76955-125">Чтобы определить значение параметра _ассетид_ , можно скопировать его из URL-адреса веб-страницы магазина Office для надстройки.</span><span class="sxs-lookup"><span data-stu-id="76955-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="76955-126">Ассетидс всегда начинается с "WA", за которым следует число.</span><span class="sxs-lookup"><span data-stu-id="76955-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="76955-127">Например, в предыдущем примере источник для значения Ассетид для WA104099688 — это URL-адрес веб-страницы магазина Office для надстройки: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="76955-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="76955-128">Значения параметра _locale_ и параметра _контентмаркет_ идентичны и указывают страну или регион, из которого вы пытаетесь установить надстройку.</span><span class="sxs-lookup"><span data-stu-id="76955-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="76955-129">Формат — en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="76955-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="76955-130">и т. д.</span><span class="sxs-lookup"><span data-stu-id="76955-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="76955-131">Надстройки, отправленные из магазина Office, автоматически обновляются в течение нескольких дней с последнего обновления, доступного в магазине Office.</span><span class="sxs-lookup"><span data-stu-id="76955-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="76955-132">Получение сведений о надстройке</span><span class="sxs-lookup"><span data-stu-id="76955-132">Get details of an add-in</span></span>

<span data-ttu-id="76955-133">Выполните командлет **Get – организатионаддин** , как показано ниже, чтобы получить сведения обо всех надстройках, отправленных в клиент, включающих идентификатор продукта надстройки.</span><span class="sxs-lookup"><span data-stu-id="76955-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="76955-134">Выполните командлет **Get – организатионаддин** со значением параметра _ProductID_ , чтобы указать, для какой надстройки необходимо получить сведения.</span><span class="sxs-lookup"><span data-stu-id="76955-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="76955-135">Чтобы получить полные сведения обо всех надстройках, а также о назначенных пользователях и группах, перечислите выходные данные командлета **Get – организатионаддин** в командлет Format – List, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="76955-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="76955-136">Включение и отключение надстройки</span><span class="sxs-lookup"><span data-stu-id="76955-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="76955-137">Чтобы отключить надстройку, чтобы пользователи и группы, которым назначена эта надстройка, больше не были доступны, выполните командлет **Set – организатионаддин** с параметром _ProductID_ и параметром _Enabled_ `$false`, равным, как показано в следующем примере. .</span><span class="sxs-lookup"><span data-stu-id="76955-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="76955-138">Чтобы снова включить надстройку, выполните тот же командлет, для `$true`параметра _Enabled_ которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="76955-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="76955-139">Добавление и удаление пользователей из надстройки</span><span class="sxs-lookup"><span data-stu-id="76955-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="76955-140">Чтобы добавить пользователей и группы в определенную надстройку, выполните командлет **Set – организатионаддинассигнментс** с параметрами _ProductID_, _Add_и Members. __</span><span class="sxs-lookup"><span data-stu-id="76955-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="76955-141">Разделяйте адреса электронной почты членов запятыми.</span><span class="sxs-lookup"><span data-stu-id="76955-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="76955-142">Чтобы удалить пользователей и группы, выполните один командлет с параметром _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="76955-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="76955-143">Чтобы назначить надстройку всем пользователям в клиенте, выполните тот же командлет с параметром _ассигнтоеверйоне_ , для `$true`которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="76955-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="76955-144">Чтобы не присваивать надстройке всем пользователям и вернуться к ранее назначенным пользователям и группам, можно выполнить один и тот же командлет и отключить параметр _ассигнтоеверйоне_ , присвоив ему значение `$false`.</span><span class="sxs-lookup"><span data-stu-id="76955-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="76955-145">Обновление надстройки</span><span class="sxs-lookup"><span data-stu-id="76955-145">Update an add-in</span></span>

<span data-ttu-id="76955-146">Чтобы обновить надстройку с помощью манифеста, выполните командлет **Set – организатионаддин** с параметрами _ProductID_, _манифестпас_и _locale_ , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="76955-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="76955-147">Надстройки, отправленные из магазина Office, автоматически обновляются в течение нескольких дней с последнего обновления, доступного в магазине Office.</span><span class="sxs-lookup"><span data-stu-id="76955-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="76955-148">Удаление надстройки</span><span class="sxs-lookup"><span data-stu-id="76955-148">Delete an add-in</span></span>

<span data-ttu-id="76955-149">Чтобы удалить надстройку, запустите командлет Remove **– организатионаддин** с параметром _ProductID_ , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="76955-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a><span data-ttu-id="76955-150">Настройка надстроек Microsoft Store для Организации</span><span class="sxs-lookup"><span data-stu-id="76955-150">Customize Microsoft Store add-ins for your organization</span></span>

<span data-ttu-id="76955-151">Перед развертыванием надстройки в Организации ее необходимо настроить.</span><span class="sxs-lookup"><span data-stu-id="76955-151">You must customize the add-in before you deploy it to your organization.</span></span> <span data-ttu-id="76955-152">Надстройки более ранние, чем версия 1,1, не поддерживаются этой функцией.</span><span class="sxs-lookup"><span data-stu-id="76955-152">Add-ins older than version 1.1 are not supported by this feature.</span></span> 

<span data-ttu-id="76955-153">Кроме того, обратите внимание на следующие ограничения:</span><span class="sxs-lookup"><span data-stu-id="76955-153">Note also the following restrictions:</span></span>
- <span data-ttu-id="76955-154">Все URL-адреса должны быть абсолютными (включая HTTP или HTTPS) и допустимыми.</span><span class="sxs-lookup"><span data-stu-id="76955-154">All URLs must be absolute (include http or https) and valid.</span></span>
- <span data-ttu-id="76955-155">*Отображаемое имя* не должно превышать 125 символов</span><span class="sxs-lookup"><span data-stu-id="76955-155">*DisplayName* must not exceed 125 characters</span></span> 
- <span data-ttu-id="76955-156">*DisplayName*, *ресурсы* и *AppDomain* не должны содержать следующие символы:</span><span class="sxs-lookup"><span data-stu-id="76955-156">*DisplayName*, *Resources* and *AppDomains* must not include the following characters:</span></span> 
 
    - \<
    -  \>
    -  <span data-ttu-id="76955-157">;</span><span class="sxs-lookup"><span data-stu-id="76955-157"></span></span>
    -  =   

<span data-ttu-id="76955-158">Если вы хотите настроить развернутую надстройку, необходимо удалить ее из центра администрирования, а затем удалить надстройку из [локального кэша](#remove-an-add-in-from-local-cache) , чтобы удалить ее с каждого компьютера, на котором она была развернута.</span><span class="sxs-lookup"><span data-stu-id="76955-158">If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.</span></span>

<span data-ttu-id="76955-159">Чтобы настроить надстройку, выполните командлет **Set – организатионаддиноверридес** с *ProductID* в качестве параметра, а затем тег, который необходимо перезаписать, и новое значение.</span><span class="sxs-lookup"><span data-stu-id="76955-159">To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value.</span></span> <span data-ttu-id="76955-160">Чтобы узнать, как получить код *продукта* , ознакомьтесь со статьей [Получение сведений о надстройке](#get-details-of-an-add-in) в этой статье.</span><span class="sxs-lookup"><span data-stu-id="76955-160">To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article.</span></span> <span data-ttu-id="76955-161">Пример:</span><span class="sxs-lookup"><span data-stu-id="76955-161">For example:</span></span>

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
<span data-ttu-id="76955-162">Чтобы настроить несколько тегов для надстройки, добавьте эти теги в командную строку:</span><span class="sxs-lookup"><span data-stu-id="76955-162">To customize multiple tags for an add-in, add those tags to the commandline:</span></span>

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> <span data-ttu-id="76955-163">К одной надстройке необходимо применить несколько настраиваемых тегов с одной командой.</span><span class="sxs-lookup"><span data-stu-id="76955-163">You must apply multiple customized tags to one add-in as one command.</span></span> <span data-ttu-id="76955-164">Если вы настраиваете Теги один на один, то применяется только последняя настройка.</span><span class="sxs-lookup"><span data-stu-id="76955-164">If you customize tags one by one, only the last customization will be applied.</span></span> <span data-ttu-id="76955-165">Кроме того, если вы настраиваете тег по ошибке, необходимо удалить все настройки и начать заново.</span><span class="sxs-lookup"><span data-stu-id="76955-165">Additionally, if you customize a tag by mistake, you must remove all customizations and start over.</span></span>

### <a name="tags-you-can-customize"></a><span data-ttu-id="76955-166">Теги, которые можно настраивать</span><span class="sxs-lookup"><span data-stu-id="76955-166">Tags you can customize</span></span>

| <span data-ttu-id="76955-167">Tag</span><span class="sxs-lookup"><span data-stu-id="76955-167">Tag</span></span>                  | <span data-ttu-id="76955-168">Описание</span><span class="sxs-lookup"><span data-stu-id="76955-168">Description</span></span>          |
| :------------------- | :------------------- |
| <span data-ttu-id="76955-169">\<IconURL></span><span class="sxs-lookup"><span data-stu-id="76955-169">\<IconURL></span></span>   </br>| <span data-ttu-id="76955-170">URL-адрес изображения, используемого в качестве значка надстройки (в центре администрирования).</span><span class="sxs-lookup"><span data-stu-id="76955-170">The URL of the image used as the add-in’s icon (in admin center).</span></span> </br> |
| <span data-ttu-id="76955-171">\<DisplayName></span><span class="sxs-lookup"><span data-stu-id="76955-171">\<DisplayName></span></span>| <span data-ttu-id="76955-172">Название надстройки (в центре администрирования).</span><span class="sxs-lookup"><span data-stu-id="76955-172">The title of the add-in  (in admin center).</span></span>|
| <span data-ttu-id="76955-173">\<Hosts></span><span class="sxs-lookup"><span data-stu-id="76955-173">\<Hosts></span></span>| <span data-ttu-id="76955-174">Список приложений, которые будут поддерживать надстройку.</span><span class="sxs-lookup"><span data-stu-id="76955-174">List of apps that will support the add-in.</span></span>|
| <span data-ttu-id="76955-175">\<SourceLocation></span><span class="sxs-lookup"><span data-stu-id="76955-175">\<SourceLocation></span></span> | <span data-ttu-id="76955-176">URL-адрес источника, к которому будет подключаться надстройка.</span><span class="sxs-lookup"><span data-stu-id="76955-176">The source URL that the add-in will connect to.</span></span>| 
| <span data-ttu-id="76955-177">\<> AppDomains</span><span class="sxs-lookup"><span data-stu-id="76955-177">\<AppDomains></span></span> | <span data-ttu-id="76955-178">Список доменов, с которыми может подключаться надстройка.</span><span class="sxs-lookup"><span data-stu-id="76955-178">A list of domains that the add-in can connect with.</span></span> | 
| <span data-ttu-id="76955-179">\<SupportURL></span><span class="sxs-lookup"><span data-stu-id="76955-179">\<SupportURL></span></span>| <span data-ttu-id="76955-180">URL-адрес, с помощью которого пользователи могут получать доступ к справке и поддержке.</span><span class="sxs-lookup"><span data-stu-id="76955-180">The URL users can use to access help and support.</span></span> | 
| <span data-ttu-id="76955-181">\<Ресурсы></span><span class="sxs-lookup"><span data-stu-id="76955-181">\<Resources></span></span>  | <span data-ttu-id="76955-182">Этот тег содержит ряд элементов, в том числе заголовки, подсказки и значки разного размера.</span><span class="sxs-lookup"><span data-stu-id="76955-182">This tag contains a number of elements including titles, tooltips, and icons of different sizes.</span></span>| 
|
### <a name="customize-resources-tag"></a><span data-ttu-id="76955-183">Настройка тега Resources</span><span class="sxs-lookup"><span data-stu-id="76955-183">Customize Resources tag</span></span>

<span data-ttu-id="76955-184">Любой элемент в <Resources> теге манифеста может быть динамически настраиваемым.</span><span class="sxs-lookup"><span data-stu-id="76955-184">Any element in the <Resources> tag of the manifest can be customized dynamically.</span></span> <span data-ttu-id="76955-185">Сначала необходимо проверить манифест, чтобы найти идентификатор элемента, которому требуется назначить новое значение.</span><span class="sxs-lookup"><span data-stu-id="76955-185">You first need to check the manifest to find the element id to which you want to assign a new value.</span></span> <span data-ttu-id="76955-186"><Resources> Тег выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="76955-186">The <Resources> tag looks like this:</span></span>

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
<span data-ttu-id="76955-187">В этом случае идентификатор элемента изображения — "img16icon", а связанное с ним значение — "http:<i></i>//Сите. <i> </i>com/IMG. jpg. "</span><span class="sxs-lookup"><span data-stu-id="76955-187">In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”</span></span>

<span data-ttu-id="76955-188">Определив элементы, которые вы хотите настроить, выполните следующую команду в PowerShell, чтобы присвоить элементам новые значения:</span><span class="sxs-lookup"><span data-stu-id="76955-188">Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:</span></span>

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

<span data-ttu-id="76955-189">Вы можете настроить любое количество элементов с помощью команды.</span><span class="sxs-lookup"><span data-stu-id="76955-189">You can customize as many elements with the command as you need to.</span></span>

### <a name="remove-customization-from-an-add-in"></a><span data-ttu-id="76955-190">Удаление настроек из надстройки</span><span class="sxs-lookup"><span data-stu-id="76955-190">Remove customization from an add-in</span></span>

<span data-ttu-id="76955-191">Единственным вариантом, доступным для удаления настроек, является удаление всех из них одновременно:</span><span class="sxs-lookup"><span data-stu-id="76955-191">The only option currently available for deleting customizations is to delete all of them at once:</span></span>

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a><span data-ttu-id="76955-192">Просмотр настроек надстроек</span><span class="sxs-lookup"><span data-stu-id="76955-192">View add-in customizations</span></span>

<span data-ttu-id="76955-193">Чтобы просмотреть список примененных настроек, выполните командлет **Get – организатионаддиноверридес** .</span><span class="sxs-lookup"><span data-stu-id="76955-193">To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet.</span></span> <span data-ttu-id="76955-194">Если командлет **Get-организатионаддиноверридес** запускается без *ProductID* , возвращается список всех надстроек с примененными переопределениями.</span><span class="sxs-lookup"><span data-stu-id="76955-194">If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.</span></span>  

```powershell
Get-OrganizationAddInOverrides 
```
<span data-ttu-id="76955-195">Если указан ProductId, возвращается список переопределений, примененных к этой надстройке.</span><span class="sxs-lookup"><span data-stu-id="76955-195">If ProductId is specified, then a list of overrides applied to that add-in is returned.</span></span> 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a><span data-ttu-id="76955-196">Удаление надстройки из локального кэша</span><span class="sxs-lookup"><span data-stu-id="76955-196">Remove an add-in from local cache</span></span>

<span data-ttu-id="76955-197">Если надстройка была развернута, ее необходимо удалить из кэша на каждом компьютере перед настройкой.</span><span class="sxs-lookup"><span data-stu-id="76955-197">If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized.</span></span> <span data-ttu-id="76955-198">Чтобы ремиве надстройку из кэша:</span><span class="sxs-lookup"><span data-stu-id="76955-198">To remive an add-in from cache:</span></span>

1. <span data-ttu-id="76955-199">Переход к папке "Пользователи" в C:</span><span class="sxs-lookup"><span data-stu-id="76955-199">Navigate to the “Users” folder in C:</span></span>\ 
1. <span data-ttu-id="76955-200">Переход к папке пользователя</span><span class="sxs-lookup"><span data-stu-id="76955-200">Go to your user folder</span></span>
1. <span data-ttu-id="76955-201">Перейдите к Аппдата\локал\микрософт\оффице и выберите папку, связанную с версией Office.</span><span class="sxs-lookup"><span data-stu-id="76955-201">Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office</span></span>
1. <span data-ttu-id="76955-202">В папке *WEF* удалите папку *манифестов* .</span><span class="sxs-lookup"><span data-stu-id="76955-202">In the *Wef* folder delete the *Manifests* folder.</span></span>

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="76955-203">Получение подробной справки для каждого командлета</span><span class="sxs-lookup"><span data-stu-id="76955-203">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="76955-204">С помощью командлета Get – Help можно просмотреть подробную справку для каждого командлета.</span><span class="sxs-lookup"><span data-stu-id="76955-204">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="76955-205">Например, следующий командлет предоставляет подробные сведения о командлете Remove – Организатионаддин.</span><span class="sxs-lookup"><span data-stu-id="76955-205">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


