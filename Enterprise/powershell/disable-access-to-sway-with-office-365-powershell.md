---
title: "Отключение доступа к Sway с помощью PowerShell в Office 365"
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
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: "Узнайте, как загрузить сценарий ManageSway.ps1 PowerShell, который позволяет запретить доступ к Sway в вашей организации Office 365:."
ms.openlocfilehash: c27aaa7006fa0e29644b11ebc53c0d50e0d97fda
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-sway-with-office-365-powershell"></a><span data-ttu-id="71d00-103">Отключение доступа к Sway с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="71d00-103">Disable access to Sway with Office 365 PowerShell</span></span>

<span data-ttu-id="71d00-104">**Сводка** Используйте сценарий ManageSway.ps1 PowerShell, чтобы отключить доступ к Sway в организации Office 365.</span><span class="sxs-lookup"><span data-stu-id="71d00-104">**Summary** Use the ManageSway.ps1 PowerShell script to disable access to Sway in your Office 365 organization.</span></span>
  
<span data-ttu-id="71d00-p101">Этот сценарий позволяет просматривать и отключать службы в вашей организации Office 365:, в том числе Sway. Данный сценарий позволяет автоматизировать процедуры, описанные в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="71d00-p101">The ManageSway.ps1 PowerShell script allows you to view and disable services in your Office 365 organization, including Sway. This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="71d00-107">Просмотр лицензий и служб с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="71d00-107">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="71d00-108">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="71d00-108">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="71d00-109">Необходимо загрузить два файла, связанные со сценарием:</span><span class="sxs-lookup"><span data-stu-id="71d00-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="71d00-110">Сценарий ManageSway.ps1 на [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span><span class="sxs-lookup"><span data-stu-id="71d00-110">The ManageSway.ps1 script at [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span></span>
    
- <span data-ttu-id="71d00-111">Файл справки для сценария, в [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span><span class="sxs-lookup"><span data-stu-id="71d00-111">The help file for the script at [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span></span>
    

