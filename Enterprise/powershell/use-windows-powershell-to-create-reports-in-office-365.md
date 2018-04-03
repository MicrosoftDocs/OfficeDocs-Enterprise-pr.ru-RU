---
title: Использование Windows PowerShell для создания отчетов в Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: Сводка. В этой статье рассказано, как с помощью PowerShell в Office 365 создавать отчеты, которые невозможно создать в Центре администрирования Office 365:.
ms.openlocfilehash: 09db143c027af987cf86036c4f5fd6bca009afe4
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="use-windows-powershell-to-create-reports-in-office-365"></a><span data-ttu-id="2c0b0-103">Использование Windows PowerShell для создания отчетов в Office 365</span><span class="sxs-lookup"><span data-stu-id="2c0b0-103">Use Windows PowerShell to create reports in Office 365</span></span>

 <span data-ttu-id="2c0b0-104">**Сводка.** Создавайте отчеты, которые нельзя создать в Центре администрирования Office 365, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-104">**Summary:** Use Office 365 PowerShell to create reports that you cannot produce in the Office 365 Admin center.</span></span>
  
<span data-ttu-id="2c0b0-p101">В Центре администрирования Office 365: доступно множество различных отчетов. Тем не менее иногда представленной в них информации бывает недостаточно. В таких случаях на помощь приходит PowerShell в Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-p101">There are many different reports available in the Office 365 Admin center. However, these reports only provide so much information and sometimes you need more. That's when you need Office 365 PowerShell</span></span>
  
<span data-ttu-id="2c0b0-108">В этих статьях описано, как использовать PowerShell в Office 365 для получения данных клиента Office 365:.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-108">These articles that describe how to use Office 365 PowerShell to obtain information from your Office 365 tenant:</span></span>
  
- <span data-ttu-id="2c0b0-109">Начало работы с составлением отчетов в PowerShell в Office 365:</span><span class="sxs-lookup"><span data-stu-id="2c0b0-109">Getting started with reporting using Office 365 PowerShell:</span></span>
    
  - <span data-ttu-id="2c0b0-110">[С помощью PowerShell в Office 365 можно получить дополнительную информацию, которая недоступна в Центре администрирования](https://technet.microsoft.com/library/dn568034.aspx#reveal).</span><span class="sxs-lookup"><span data-stu-id="2c0b0-110">[Office 365 PowerShell can reveal additional information that you cannot see with the Admin center](https://technet.microsoft.com/library/dn568034.aspx#reveal)</span></span>
    
  - <span data-ttu-id="2c0b0-111">[PowerShell в Office 365 прекрасно подходит для фильтрации данных](https://technet.microsoft.com/library/dn568034.aspx#filter).</span><span class="sxs-lookup"><span data-stu-id="2c0b0-111">[Office 365 PowerShell is great at filtering data](https://technet.microsoft.com/library/dn568034.aspx#filter)</span></span>
    
  - <span data-ttu-id="2c0b0-112">[PowerShell в Office 365 упрощает процесс печати и сохранения данных](https://technet.microsoft.com/library/dn568034.aspx#printsave).</span><span class="sxs-lookup"><span data-stu-id="2c0b0-112">[Office 365 PowerShell makes it easy to print or save data](https://technet.microsoft.com/library/dn568034.aspx#printsave)</span></span>
    
- <span data-ttu-id="2c0b0-113">Отчеты для пользовательских учетных записей и лицензий:</span><span class="sxs-lookup"><span data-stu-id="2c0b0-113">Reports for user accounts and licenses:</span></span>
    
  - <span data-ttu-id="2c0b0-114">[Просмотр лицензий и служб с помощью PowerShell в Office 365](view-licenses-and-services-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="2c0b0-114">[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)</span></span>
    
  - <span data-ttu-id="2c0b0-115">[Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="2c0b0-115">[View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)</span></span>
    
  - <span data-ttu-id="2c0b0-116">[Просмотр сведений о лицензии и службе учетной записи с помощью PowerShell в Office 365](view-account-license-and-service-details-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="2c0b0-116">[View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)</span></span>
    
  - <span data-ttu-id="2c0b0-117">[Просмотр учетных записей пользователей с помощью PowerShell для Office 365](view-user-accounts-with-office-365-powershell.md) .</span><span class="sxs-lookup"><span data-stu-id="2c0b0-117">[View user accounts with Office 365 PowerShell](view-user-accounts-with-office-365-powershell.md)</span></span>
    
- <span data-ttu-id="2c0b0-118">Отчеты для SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="2c0b0-118">Reports for SharePoint Online:</span></span>
    
  - <span data-ttu-id="2c0b0-119">[Управление пользователями и группами SharePoint Online с помощью Office 365 PowerShell](http://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx) .</span><span class="sxs-lookup"><span data-stu-id="2c0b0-119">[Manage SharePoint Online users and groups with Office 365 PowerShell](http://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx)</span></span>
    
  - <span data-ttu-id="2c0b0-120">[Manage SharePoint Online site groups with Office 365 PowerShell](http://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx).</span><span class="sxs-lookup"><span data-stu-id="2c0b0-120">[Manage SharePoint Online site groups with Office 365 PowerShell](http://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)</span></span>
    
- <span data-ttu-id="2c0b0-121">Отчеты для Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="2c0b0-121">Reports for Exchange Online:</span></span>
    
  - <span data-ttu-id="2c0b0-122">[Display Exchange Online mailbox information with Office 365 PowerShell](http://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx).</span><span class="sxs-lookup"><span data-stu-id="2c0b0-122">[Display Exchange Online mailbox information with Office 365 PowerShell](http://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)</span></span>
    
  - <span data-ttu-id="2c0b0-123">[Display Exchange Online reports with Office 365 PowerShell](http://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx).</span><span class="sxs-lookup"><span data-stu-id="2c0b0-123">[Display Exchange Online reports with Office 365 PowerShell](http://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)</span></span>
    
## <a name="see-also"></a><span data-ttu-id="2c0b0-124">См. также</span><span class="sxs-lookup"><span data-stu-id="2c0b0-124">See also</span></span>

#### 

[<span data-ttu-id="2c0b0-125">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="2c0b0-125">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2c0b0-126">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c0b0-126">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="2c0b0-127">Управление SharePoint Online с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c0b0-127">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="2c0b0-128">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c0b0-128">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="2c0b0-129">Использование Excel для получения отчетных данных Office 365</span><span class="sxs-lookup"><span data-stu-id="2c0b0-129">Using Excel to Retrieve Office 365 Reporting Data</span></span>](using-excel-to-retrieve-office-365-reporting-data.md)

