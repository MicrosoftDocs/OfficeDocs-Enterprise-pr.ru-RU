---
title: Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: В этой статье рассказывается, как использовать PowerShell в Office 365 для просмотра учетных записей пользователей с лицензиями и пользователей без лицензий.
ms.openlocfilehash: 61f94664a62b6a5cb178579c1a5777b208d0b2ec
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123366"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="a458a-103">Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a458a-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="a458a-104">**Сводка.** Узнайте, как просмотреть учетные записи пользователей Office 365 с лицензиями и без них, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a458a-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="a458a-p101">Учетным записям пользователей в вашей организации Office 365: могут быть назначены все лицензии или часть лицензий (или вообще ни одной доступной лицензии) из планов лицензирования, имеющихся в организации. С помощью PowerShell в Office 365 вы можете быстро найти пользователей в организации, у которых есть лицензии, и пользователей, у которых их нет.</span><span class="sxs-lookup"><span data-stu-id="a458a-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="a458a-107">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="a458a-107">Before you begin</span></span>

- <span data-ttu-id="a458a-p102">Для процедур, описанных в этой статье, требуется подключение к PowerShell в Office 365. Указания см. в статье [Подключение к Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a458a-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a458a-110">Если использовать командлет **Get-MsolUser** без параметра _-All_, возвращаются только первые 500 учетных записей.</span><span class="sxs-lookup"><span data-stu-id="a458a-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="viewing-licensed-and-unlicensed-users"></a><span data-ttu-id="a458a-111">Просмотр лицензионной и нелицензированных пользователей</span><span class="sxs-lookup"><span data-stu-id="a458a-111">Viewing licensed and unlicensed users</span></span>

<span data-ttu-id="a458a-112">Чтобы отобразить список всех учетных записей пользователей в организации и сведения об их состояниях лицензирования, в PowerShell в Office 365 выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="a458a-112">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="a458a-113">Чтобы отобразить список всех учетных записей пользователей без лицензий в вашей организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="a458a-113">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="a458a-114">Чтобы отобразить список всех учетных записей пользователей с лицензиями в вашей организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="a458a-114">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="a458a-115">См. также</span><span class="sxs-lookup"><span data-stu-id="a458a-115">See also</span></span>

<span data-ttu-id="a458a-116">Дополнительные сведения о командлетах, использованных в этих процедурах, см. в указанных ниже статьях.</span><span class="sxs-lookup"><span data-stu-id="a458a-116">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="a458a-117">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a458a-117">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="a458a-118">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a458a-118">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

