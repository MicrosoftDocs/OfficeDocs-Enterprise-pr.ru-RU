---
title: Отключение доступа к Sway с помощью PowerShell для Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: Узнайте, где скачать скрипт ManageSway.ps1 PowerShell, который позволяет отключить доступ к Sway в организации Microsoft 365.
ms.openlocfilehash: d02a197e2767a1883abcc8fcb4074f3ac92de88a
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230705"
---
# <a name="disable-access-to-sway-with-powershell-for-microsoft-365"></a><span data-ttu-id="dbd98-103">Отключение доступа к Sway с помощью PowerShell для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="dbd98-103">Disable access to Sway with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="dbd98-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="dbd98-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="dbd98-105">ManageSway.ps1 скрипт PowerShell позволяет просматривать и отключать службы в организации Microsoft 365, в том числе Sway.</span><span class="sxs-lookup"><span data-stu-id="dbd98-105">The ManageSway.ps1 PowerShell script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="dbd98-106">Данный сценарий позволяет автоматизировать процедуры, описанные в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="dbd98-106">This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="dbd98-107">Просмотр лицензий и служб с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbd98-107">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="dbd98-108">Отключение доступа к службам с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbd98-108">Disable access to services with PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="dbd98-109">Необходимо загрузить два файла, связанные со сценарием:</span><span class="sxs-lookup"><span data-stu-id="dbd98-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="dbd98-110">Сценарий ManageSway.ps1: [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span><span class="sxs-lookup"><span data-stu-id="dbd98-110">The ManageSway.ps1 script at [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span></span>
    
- <span data-ttu-id="dbd98-111">Файл справки для сценария: [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span><span class="sxs-lookup"><span data-stu-id="dbd98-111">The help file for the script at [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span></span>
    

