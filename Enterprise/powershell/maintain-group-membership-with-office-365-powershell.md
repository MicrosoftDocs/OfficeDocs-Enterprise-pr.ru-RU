---
title: Управление членством в группах с помощью PowerShell для Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
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
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Узнайте, как использовать PowerShell для Office 365 для поддержки членства в группах для Office 365.
ms.openlocfilehash: 0e6c5f2e27f9d146bb2a053bd3bdb6694fb07276
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004632"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="c8088-103">Управление членством в группах с помощью PowerShell для Office 365</span><span class="sxs-lookup"><span data-stu-id="c8088-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="c8088-104">Вы можете использовать Office 365 PowerShell в качестве альтернативы центру администрирования Microsoft 365 для поддержки членства в группах в Office 365.</span><span class="sxs-lookup"><span data-stu-id="c8088-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="c8088-105">Чтобы создать готовые команды PowerShell, указав имена учетных записей пользователей и групп, используйте эту [книгу для обслуживания групп Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span><span class="sxs-lookup"><span data-stu-id="c8088-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c8088-106">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="c8088-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="c8088-107">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="c8088-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="c8088-108">Добавление и удаление учетных записей пользователей в качестве участников группы</span><span class="sxs-lookup"><span data-stu-id="c8088-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="c8088-109">**Чтобы добавить учетную запись пользователя по имени участника**-пользователя, заполните имя участника-пользователя для учетной записи пользователя (например: belindan@contoso.com) и отображаемое имя группы, удалите символы "<" и ">", а затем выполните следующие команды в окне PowerShell или интегрированной среде сценариев POWERSHELL (ISE).</span><span class="sxs-lookup"><span data-stu-id="c8088-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c8088-110">**Чтобы добавить учетную запись пользователя по отображаемому имени**, заполните отображаемое имя учетной записи пользователя (например, Светланы Коноваловой) и отображаемое имя группы, а затем выполните указанные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c8088-111">**Чтобы удалить учетную запись пользователя по имени участника**-пользователя, введите имя участника-пользователя (например: belindan@contoso.com) и отображаемое имя группы, а затем выполните приведенные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c8088-112">**Чтобы удалить учетную запись пользователя по отображаемому имени**, заполните отображаемое имя учетной записи пользователя (например, Светланы Коноваловой) и отображаемое имя группы, а затем выполните указанные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="c8088-113">Добавление и удаление групп в качестве участников группы</span><span class="sxs-lookup"><span data-stu-id="c8088-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="c8088-114">Группы безопасности могут содержать другие группы в качестве участников.</span><span class="sxs-lookup"><span data-stu-id="c8088-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="c8088-115">Однако группы Office 365 не могут.</span><span class="sxs-lookup"><span data-stu-id="c8088-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="c8088-116">В этом разделе содержатся команды PowerShell для добавления или удаления групп только для группы безопасности.</span><span class="sxs-lookup"><span data-stu-id="c8088-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="c8088-117">**Чтобы добавить группу по отображаемому имени**, укажите отображаемое имя добавляемой группы и отображаемое имя группы, которая будет содержать группу участников, и выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c8088-118">**Чтобы удалить группу по отображаемому имени**, укажите отображаемое имя группы, которую нужно удалить, и отображаемое имя группы, которая будет содержать группу участников, и выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c8088-119">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8088-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c8088-120">Сначала [подключитесь к своему клиенту Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c8088-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="c8088-121">Добавление и удаление учетных записей пользователей в качестве участников группы</span><span class="sxs-lookup"><span data-stu-id="c8088-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="c8088-122">**Чтобы добавить учетную запись пользователя по имени участника**-пользователя, заполните имя участника-пользователя для учетной записи пользователя (например: belindan@contoso.com) и отображаемое имя группы, удалите символы "<" и ">", а затем выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c8088-123">**Чтобы добавить учетную запись пользователя по отображаемому имени**, заполните отображаемое имя учетной записи пользователя (например, Светланы Коноваловой) и отображаемое имя группы, а затем выполните указанные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c8088-124">**Чтобы удалить учетную запись пользователя по имени участника**-пользователя, введите имя участника-пользователя (например: belindan@contoso.com) и отображаемое имя группы, а затем выполните приведенные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c8088-125">**Чтобы удалить учетную запись пользователя по отображаемому имени**, заполните отображаемое имя учетной записи пользователя (например, Светланы Коноваловой) и отображаемое имя группы, а затем выполните указанные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="c8088-126">Добавление и удаление групп в качестве участников группы</span><span class="sxs-lookup"><span data-stu-id="c8088-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="c8088-127">Группы безопасности могут содержать другие группы в качестве участников.</span><span class="sxs-lookup"><span data-stu-id="c8088-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="c8088-128">Однако группы Office 365 не могут.</span><span class="sxs-lookup"><span data-stu-id="c8088-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="c8088-129">В этом разделе содержатся команды PowerShell для добавления или удаления групп только для группы безопасности.</span><span class="sxs-lookup"><span data-stu-id="c8088-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="c8088-130">**Чтобы добавить группу по отображаемому имени**, укажите отображаемое имя добавляемой группы и отображаемое имя группы, которая будет содержать группу участников, и выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="c8088-131">**Чтобы удалить группу по отображаемому имени**, укажите отображаемое имя группы, которую нужно удалить, и отображаемое имя группы, которая будет содержать группу участников, и выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8088-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="c8088-132">См. также</span><span class="sxs-lookup"><span data-stu-id="c8088-132">See also</span></span>

[<span data-ttu-id="c8088-133">Управление учетными записями пользователей, лицензиями и группами с помощью Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8088-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c8088-134">Управление Office 365 с помощью PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="c8088-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c8088-135">Начало работы с Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8088-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

