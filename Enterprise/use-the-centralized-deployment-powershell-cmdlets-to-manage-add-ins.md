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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Управление надстройками с помощью командлетов PowerShell централизованного развертывания

Как администратор Office 365 надстроек Office можно развернуть для пользователей с помощью централизованного развертывания (см [надстроек развертывания Office в центре администрирования Office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). В дополнение к развертыванию надстроек Office с помощью центра администрирования Office 365, можно также использовать Microsoft PowerShell. [Загрузите](https://go.microsoft.com/fwlink/p/?linkid=850850) командлеты PowerShell централизованного развертывания из центра загрузки Майкрософт. 
    
## <a name="connect-using-your-admin-credentials"></a>Подключиться, используя свои учетные данные администратора

Прежде чем использовать командлеты централизованного развертывания, необходимо выполнить вход.
  
1. Запустите PowerShell.
    
2. Подключение к PowerShell с помощью свои учетные данные администратора компании. Выполните следующий командлет.
    
  ```
  Connect-OrganizationAddInService
  ```

3. На странице **Ввода учетных данных** введите учетные данные глобального администратора Office 365. Кроме того можно ввести учетные данные непосредственно в командлет. 
    
    Выполните следующий командлет, определяющее вашей компании учетные данные администратора как объект PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Дополнительные сведения об использовании PowerShell можно [подключиться к Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Отправка файла манифеста надстройки

Выполните командлет New-OrganizationAdd-в Отправка файла манифеста надстройки из пути, который может быть расположение файла или URL-адрес. В следующем примере показано расположение файла для значения параметра _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Также можно запустить командлет New-OrganizationAdd-связи для загрузки надстройки и назначения ее к пользователям или группам непосредственно с помощью параметра _члены_ , как показано в следующем примере. Адреса электронной почты членов разделяются точкой с запятой. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Загрузка надстройки уровня приложения из магазина Office

Выполните командлет New-OrganizationAddIn для загрузки манифеста из магазина Office.
  
В следующем примере командлет New-OrganizationAddIn указывает значением код для надстройки для США расположение и содержимое рынка.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Чтобы определить значение параметра _значением код_ , можно скопировать из URL-адрес в магазин Office веб-страницы для AssetIds надстройки всегда начинаются с «WA», за которым следует номер. Например, в предыдущем примере источник значение значением код WA104099688 — URL-адрес веб-страницы магазина Office для надстройки: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Значения для параметра _языковой стандарт_ и параметр _ContentMarket_ идентичны и указания страны или региона, вы пытаетесь установить надстройку из. Имеет формат en US, fr-FR. и т. д. 
  
> [!NOTE]
> Надстройки, загруженные из магазина Office будет обновляться автоматически в течение нескольких дней Последние обновления, доступные в магазине Office. 
  
## <a name="get-details-of-an-add-in"></a>Подробные сведения о надстройки

Выполните командлет Get-OrganizationAddIn, как показано ниже для получения сведений о всех надстройках загружаться в клиент включенные надстройки ИД продукта.
  
```
Get-OrganizationAddIn
```

Выполните командлет Get-OrganizationAddIn значение для параметра _ProductId_ , определение которого надстройки, которую необходимо получить подробные сведения по. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Чтобы получить полные сведения о всех надстроек, а также для пользователей и групп, выходные данные командлета Get-OrganizationAddIn в командлет Format-List, как показано в следующем примере.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Включить или отключить надстройку

Чтобы отключить надстройку, пользователи и группы, назначенных на него больше не будет предоставляться доступ, выполните командлет Set-OrganizationAddIn с помощью параметра _ProductId_ и задайте параметра _Enabled_ `$false`, как показано в следующем примере.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Чтобы включить надстройку, выполните командлет же с помощью параметра _Enabled_ , задайте значение `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Добавление и удаление пользователей из надстройки

Добавление пользователей и групп для конкретных надстройки, выполните командлет Set-OrganizationAddInAssignments вместе с параметрами _ProductId_, _Добавить_, а также _элементы_ . Адреса электронной почты членов разделяются точкой с запятой. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Чтобы удалить пользователей и групп, выполните командлет же с помощью параметра _удаления_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Чтобы назначить надстройки всем пользователям, включенным клиента, выполните командлет же с помощью параметра _AssignToEveryone_ со значением, равным `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Не назначить надстройки для всеобщего доступа и вернуться к ранее для пользователей и групп, можно запустить командлет же и отключите параметр _AssignToEveryone_ , значение `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Обновление надстроек

Для обновления надстройки уровня приложения из манифеста, выполните командлет Set-OrganizationAddIn с _ProductId_, _ManifestPath_и параметры _языкового стандарта_ , как показано в следующем примере. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Надстройки, загруженные из магазина Office будет обновляться автоматически в течение нескольких дней Последние обновления, доступные в магазине Office. 
  
## <a name="delete-an-add-in"></a>Удаление надстройки

Чтобы удалить надстройку, выполните командлет Remove-OrganizationAddIn с параметром _ProductId_ , как показано в следующем примере. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Получите подробные справки для каждого командлета

Подробные справки для каждого командлета можно просмотреть с помощью командлета Get-help. Например следующий командлет предоставляет подробные сведения о командлет Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


