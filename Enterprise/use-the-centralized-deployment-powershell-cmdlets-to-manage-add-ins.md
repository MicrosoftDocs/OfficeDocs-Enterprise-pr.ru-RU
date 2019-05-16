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
ms.openlocfilehash: 34040d11a1ef4d5da2d7a0e980b28e7ef0eba7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070505"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Использование командлетов PowerShell для централизованного развертывания для управления надстройками

Администраторы Office 365 могут развертывать надстройки Office для пользователей с помощью функции централизованного развертывания (см. раздел [Развертывание надстроек Office в центре администрирования office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Кроме развертывания надстроек Office с помощью центра администрирования Office 365, вы также можете использовать Microsoft PowerShell. Установите [модуль развертывания Office 365 с централизованной надстройкой для Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 
    
## <a name="connect-using-your-admin-credentials"></a>Подключение с использованием учетных данных администратора

Прежде чем использовать командлеты централизованного развертывания, необходимо войти в систему.
  
1. Запустите PowerShell.
    
2. Подключитесь к PowerShell с помощью учетных данных администратора компании. Выполните следующий командлет.
    
  ```
  Connect-OrganizationAddInService
  ```

3. На странице **введите учетные данные** введите учетные данные глобального администратора Office 365. Кроме того, вы можете ввести свои учетные данные непосредственно в командлет. 
    
    Выполните следующий командлет, указав учетные данные администратора компании в качестве объекта PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Дополнительные сведения об использовании PowerShell приведены в статье [Подключение к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Отправка манифеста надстройки

Выполните командлет New-Организациянадстройки-in, чтобы отправить манифест надстройки по пути, который может представлять собой расположение файла или URL-адрес. В следующем примере показано расположение файла для значения параметра _манифестпас_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Кроме того, можно выполнить командлет New – Организациянадстройки – in, чтобы отправить надстройку и назначить ее пользователям или группам напрямую с помощью параметра Members __ , как показано в следующем примере. Разделяйте адреса электронной почты членов запятыми. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Отправка надстройки из магазина Office

Выполните командлет New – Организатионаддин, чтобы отправить манифест из магазина Office.
  
В следующем примере командлет New – Организатионаддин указывает Ассетид для надстройки для местонахождения США и рынка контента.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Чтобы определить значение параметра _ассетид_ , можно скопировать его из URL-адреса веб-страницы магазина Office для надстройки. Ассетидс всегда начинается с "WA", за которым следует число. Например, в предыдущем примере источник для значения Ассетид для WA104099688 — это URL-адрес веб-страницы магазина Office для надстройки: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Значения параметра _locale_ и параметра _контентмаркет_ идентичны и указывают страну или регион, из которого вы пытаетесь установить надстройку. Формат — en-US, fr-FR. и т. д. 
  
> [!NOTE]
> Надстройки, отправленные из магазина Office, автоматически обновляются в течение нескольких дней с последнего обновления, доступного в магазине Office. 
  
## <a name="get-details-of-an-add-in"></a>Получение сведений о надстройке

Выполните командлет Get – Организатионаддин, как показано ниже, чтобы получить сведения обо всех надстройках, отправленных в клиент, включающих идентификатор продукта надстройки.
  
```
Get-OrganizationAddIn
```

Выполните командлет Get – Организатионаддин со значением параметра _ProductID_ , чтобы указать, для какой надстройки необходимо получить сведения. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Чтобы получить полные сведения обо всех надстройках, а также о назначенных пользователях и группах, перечислите выходные данные командлета Get – Организатионаддин в командлет Format – List, как показано в следующем примере.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Включение и отключение надстройки

Чтобы отключить надстройку, чтобы пользователи и группы, которым назначена эта надстройка, больше не были доступны, выполните командлет Set – Организатионаддин с параметром _ProductID_ и параметром _Enabled_ `$false`, равным, как показано в следующем примере.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Чтобы снова включить надстройку, выполните тот же командлет, для `$true`параметра _Enabled_ которого задано значение.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Добавление и удаление пользователей из надстройки

Чтобы добавить пользователей и группы в определенную надстройку, выполните командлет Set – Организатионаддинассигнментс с параметрами _ProductID_, _Add_и Members. __ Разделяйте адреса электронной почты членов запятыми. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Чтобы удалить пользователей и группы, выполните один командлет с параметром _Remove_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Чтобы назначить надстройку всем пользователям в клиенте, выполните тот же командлет с параметром _ассигнтоеверйоне_ , для `$true`которого задано значение.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Чтобы не присваивать надстройке всем пользователям и вернуться к ранее назначенным пользователям и группам, можно выполнить один и тот же командлет и отключить параметр _ассигнтоеверйоне_ , присвоив ему значение `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Обновление надстройки

Чтобы обновить надстройку с помощью манифеста, выполните командлет Set – Организатионаддин с параметрами _ProductID_, _манифестпас_и _locale_ , как показано в следующем примере. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Надстройки, отправленные из магазина Office, автоматически обновляются в течение нескольких дней с последнего обновления, доступного в магазине Office. 
  
## <a name="delete-an-add-in"></a>Удаление надстройки

Чтобы удалить надстройку, запустите командлет Remove – Организатионаддин с параметром _ProductID_ , как показано в следующем примере. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Получение подробной справки для каждого командлета

С помощью командлета Get – Help можно просмотреть подробную справку для каждого командлета. Например, следующий командлет предоставляет подробные сведения о командлете Remove – Организатионаддин.
  
```
Get-help Remove-OrganizationAddIn -Full
```


