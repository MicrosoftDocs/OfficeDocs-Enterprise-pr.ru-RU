---
title: Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: 79f7bf1966d515634c5fc038db650c19547259aa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730344"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="45a5a-103">Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="45a5a-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="45a5a-104">**Сводка.** Узнайте, как просмотреть учетные записи пользователей Office 365 с лицензиями и без них, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45a5a-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="45a5a-p101">Учетным записям пользователей в вашей организации Office 365: могут быть назначены все лицензии или часть лицензий (или вообще ни одной доступной лицензии) из планов лицензирования, имеющихся в организации. С помощью PowerShell в Office 365 вы можете быстро найти пользователей в организации, у которых есть лицензии, и пользователей, у которых их нет.</span><span class="sxs-lookup"><span data-stu-id="45a5a-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="45a5a-107">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="45a5a-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="45a5a-108">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="45a5a-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="45a5a-109">Чтобы просмотреть список всех учетных записей пользователей в вашей организации, которые не были назначены все планы лицензирования (нелицензированных пользователей), выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="45a5a-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="45a5a-110">Чтобы просмотреть список всех учетных записей пользователей в вашей организации, которые были присвоен лицензирования планы (лицензированных пользователей), выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="45a5a-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="45a5a-111">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="45a5a-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="45a5a-112">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="45a5a-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="45a5a-113">Чтобы отобразить список всех учетных записей пользователей в организации и сведения об их состояниях лицензирования, в PowerShell в Office 365 выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="45a5a-113">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="45a5a-114">Чтобы отобразить список всех учетных записей пользователей без лицензий в вашей организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="45a5a-114">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="45a5a-115">Чтобы отобразить список всех учетных записей пользователей с лицензиями в вашей организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="45a5a-115">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="45a5a-116">См. также</span><span class="sxs-lookup"><span data-stu-id="45a5a-116">See also</span></span>

[<span data-ttu-id="45a5a-117">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="45a5a-117">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="45a5a-118">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="45a5a-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="45a5a-119">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="45a5a-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
