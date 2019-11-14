---
title: Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/13/2019
audience: Admin
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
ms.openlocfilehash: 9bef0994d516de9c06da64969f090135aad4fa46
ms.sourcegitcommit: 16a060c0732c6234bb2ebc037786a7c4872fe686
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "38308584"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="ec689-103">Отображение списков пользователей с лицензиями и пользователей без лицензий с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec689-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="ec689-104">**Сводка.** Узнайте, как просмотреть учетные записи пользователей Office 365 с лицензиями и без них, используя PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec689-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="ec689-p101">Учетным записям пользователей в вашей организации Office 365: могут быть назначены все лицензии или часть лицензий (или вообще ни одной доступной лицензии) из планов лицензирования, имеющихся в организации. С помощью PowerShell в Office 365 вы можете быстро найти пользователей в организации, у которых есть лицензии, и пользователей, у которых их нет.</span><span class="sxs-lookup"><span data-stu-id="ec689-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ec689-107">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="ec689-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ec689-108">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ec689-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="ec689-109">Чтобы просмотреть список всех учетных записей пользователей в Организации, которым не назначены планы лицензирования (нелицензированные пользователи), выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="ec689-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="ec689-110">Чтобы просмотреть список всех учетных записей пользователей в Организации, которым были назначены планы лицензирования (лицензированные пользователи), выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="ec689-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```
>[!Note]
><span data-ttu-id="ec689-111">Чтобы получить список всех пользователей в подписке, используйте `Get-AzureAdUser -All $true` команду.</span><span class="sxs-lookup"><span data-stu-id="ec689-111">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ec689-112">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec689-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ec689-113">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ec689-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="ec689-114">Чтобы отобразить список всех учетных записей пользователей в организации и сведения об их состояниях лицензирования, в PowerShell в Office 365 выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="ec689-114">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

<span data-ttu-id="ec689-115">Чтобы отобразить список всех учетных записей пользователей без лицензий в вашей организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="ec689-115">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="ec689-116">Чтобы отобразить список всех учетных записей пользователей с лицензиями в вашей организации, выполните указанную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="ec689-116">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="ec689-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ec689-117">See also</span></span>

[<span data-ttu-id="ec689-118">Управление учетными записями и лицензиями пользователей с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec689-118">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ec689-119">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="ec689-119">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ec689-120">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec689-120">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
