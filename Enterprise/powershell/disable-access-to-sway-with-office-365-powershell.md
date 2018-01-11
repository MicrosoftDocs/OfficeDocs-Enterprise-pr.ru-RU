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
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: "Узнайте, как загрузить сценарий ManageSway.ps1 PowerShell, который позволяет запретить доступ к Sway в вашей организации Office 365:."
ms.openlocfilehash: 576e770ef6453f1b14d52af2a524a081fb0fbdb5
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="disable-access-to-sway-with-office-365-powershell"></a><span data-ttu-id="ebeaf-103">Отключение доступа к Sway с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="ebeaf-103">Disable access to Sway with Office 365 PowerShell</span></span>

<span data-ttu-id="ebeaf-104">**Сводка.** Отключите доступ к Sway в своей организации Office 365, используя сценарий PowerShell ManageSway.ps1.</span><span class="sxs-lookup"><span data-stu-id="ebeaf-104">**Summary** Use the ManageSway.ps1 PowerShell script to disable access to Sway in your Office 365 organization.</span></span>
  
<span data-ttu-id="ebeaf-p101">Этот сценарий позволяет просматривать и отключать службы в вашей организации Office 365:, в том числе Sway. Данный сценарий позволяет автоматизировать процедуры, описанные в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="ebeaf-p101">The ManageSway.ps1 PowerShell script allows you to view and disable services in your Office 365 organization, including Sway. This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="ebeaf-107">Просмотр лицензий и служб с помощью PowerShell в Office 365</span><span class="sxs-lookup"><span data-stu-id="ebeaf-107">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="ebeaf-108">Отключение доступа к службам с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebeaf-108">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="ebeaf-109">Необходимо загрузить два файла, связанные со сценарием:</span><span class="sxs-lookup"><span data-stu-id="ebeaf-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="ebeaf-110">Сценарий ManageSway.ps1: [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span><span class="sxs-lookup"><span data-stu-id="ebeaf-110">The ManageSway.ps1 script at [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span></span>
    
- <span data-ttu-id="ebeaf-111">Файл справки для сценария: [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span><span class="sxs-lookup"><span data-stu-id="ebeaf-111">The help file for the script at [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span></span>
    

