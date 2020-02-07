---
title: Управление группами сайтов SharePoint Online с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Сводка: использование PowerShell в Office 365 для управления группами сайтов SharePoint Online.'
ms.openlocfilehash: c9ae4927e3c423db5ac9da4c0e7c44fcbe091e0f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841366"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Управление группами сайтов SharePoint Online с помощью Office 365 PowerShell

Несмотря на то что вы можете использовать центр администрирования Microsoft 365, вы также можете использовать Office 365 PowerShell для управления группами сайтов SharePoint Online.

## <a name="before-you-begin"></a>Подготовка

Процедуры, описанные в этой статье, требуют подключения к SharePoint Online. Инструкции см. в статье [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Просмотр SharePoint Online с помощью PowerShell для Office 365

В центре администрирования SharePoint Online есть несколько простых в использовании способов управления группами сайтов. Например, предположим, что вы хотите просмотреть группы и членов группы для `https://litwareinc.sharepoint.com/sites/finance` сайта. Вот как это сделать.

1. В центре администрирования SharePoint щелкните **активные сайты**, а затем щелкните URL-адрес сайта.
2. На странице сайт щелкните значок **Параметры** (в верхнем правом углу страницы), а затем выберите **разрешения для сайта**.

И затем повторить процесс для следующего сайта, который необходимо просмотреть.

Чтобы получить список групп с помощью Office 365 PowerShell, можно использовать следующие команды:

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Существует два способа выполнения этого набора команд в командной строке командной консоли SharePoint Online:

- Скопируйте команды в Блокнот (или другой текстовый редактор), измените значение переменной **$siteURL** , выберите команды, а затем вставьте их в командную строку консоли управления SharePoint Online. После этого PowerShell остановится в **>>** командной консоли. Нажмите клавишу ВВОД, `foreach` чтобы выполнить команду.<br/>
- Скопируйте команды в блокнот (или другой текстовый редактор), измените значение переменной **$siteURL**, а затем сохраните этот текстовый файл с именем и расширением .ps1 в подходящей папке. После этого запустите сценарий из командной строки командной консоли SharePoint Online, указав путь и имя файла. Вот пример необходимой команды:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

В обоих случаях должно отобразиться что-то вроде этого:

![Группы сайтов SharePoint Online](media/SPO-site-groups.png)

Это все группы, созданные для сайта `https://litwareinc.sharepoint.com/sites/finance`, и все пользователи, назначенные этим группам. Имена групп обозначены желтым цветом, чтобы вы могли отличить имена групп от их участников.

Другой пример: набор команд, в котором перечислены группы и все сведения о членстве в группах для всех сайтов SharePoint Online.

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a>Дополнительные ресурсы

[Подключение к PowerShell в SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Создание сайтов и добавление пользователей в SharePoint Online с помощью Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md) .

[Управление Office 365 с помощью PowerShell Office 365](manage-office-365-with-office-365-powershell.md)
  
[Начало работы с Office 365 PowerShell](getting-started-with-office-365-powershell.md)

