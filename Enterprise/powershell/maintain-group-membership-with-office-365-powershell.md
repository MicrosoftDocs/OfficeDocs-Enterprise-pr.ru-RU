---
title: Обслуживание членства в группах Microsoft 365 с помощью PowerShell
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
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Узнайте, как использовать PowerShell для поддержания членства в группах Microsoft 365.
ms.openlocfilehash: f75587c9c50a1fce3a5abfb00ddba2845318e9c4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230655"
---
# <a name="maintain-microsoft-365-group-membership-with-powershell"></a><span data-ttu-id="bc0cc-103">Обслуживание членства в группах Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc0cc-103">Maintain Microsoft 365 group membership with PowerShell</span></span>

<span data-ttu-id="bc0cc-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="bc0cc-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="bc0cc-105">Вы можете использовать PowerShell для Microsoft 365 в качестве альтернативы центру администрирования Microsoft 365 для поддержки членства в группах в Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-105">You can use PowerShell for Microsoft 365 as an alternative to the Microsoft 365 admin center to maintain group membership in Microsoft 365.</span></span> 

> [!TIP]
> <span data-ttu-id="bc0cc-106">Чтобы создать готовые команды PowerShell, указав имена учетных записей пользователей и групп, используйте эту [книгу для обслуживания групп Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span><span class="sxs-lookup"><span data-stu-id="bc0cc-106">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="bc0cc-107">Использование модуля PowerShell Azure Active Directory для Graph</span><span class="sxs-lookup"><span data-stu-id="bc0cc-107">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="bc0cc-108">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="bc0cc-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="bc0cc-109">Добавление и удаление учетных записей пользователей в качестве участников группы</span><span class="sxs-lookup"><span data-stu-id="bc0cc-109">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="bc0cc-110">**Чтобы добавить учетную запись пользователя по имени участника**-пользователя, заполните имя участника-пользователя для учетной записи пользователя (например: belindan@contoso.com) и отображаемое имя группы, удалите символы "<" и ">", а затем выполните следующие команды в окне PowerShell или интегрированной среде сценариев POWERSHELL (ISE).</span><span class="sxs-lookup"><span data-stu-id="bc0cc-110">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="bc0cc-111">**Чтобы добавить учетную запись пользователя по отображаемому имени**, заполните отображаемое имя учетной записи пользователя (например, Светланы Коноваловой) и отображаемое имя группы, а затем выполните указанные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-111">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="bc0cc-112">**Чтобы удалить учетную запись пользователя по имени участника**-пользователя, введите имя участника-пользователя (например: belindan@contoso.com) и отображаемое имя группы, а затем выполните приведенные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-112">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="bc0cc-113">**Чтобы удалить учетную запись пользователя по отображаемому имени**, заполните отображаемое имя учетной записи пользователя (например, Светланы Коноваловой) и отображаемое имя группы, а затем выполните указанные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-113">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="bc0cc-114">Добавление и удаление групп в качестве участников группы</span><span class="sxs-lookup"><span data-stu-id="bc0cc-114">Add or remove groups as members of a group</span></span>

<span data-ttu-id="bc0cc-115">Группы безопасности могут содержать другие группы в качестве участников.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-115">Security groups can contain other groups as members.</span></span> <span data-ttu-id="bc0cc-116">Однако группы Microsoft 365 не могут.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-116">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="bc0cc-117">В этом разделе содержатся команды PowerShell для добавления или удаления групп только для группы безопасности.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-117">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="bc0cc-118">**Чтобы добавить группу по отображаемому имени**, укажите отображаемое имя добавляемой группы и отображаемое имя группы, которая будет содержать группу участников, и выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-118">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="bc0cc-119">**Чтобы удалить группу по отображаемому имени**, укажите отображаемое имя группы, которую нужно удалить, и отображаемое имя группы, которая будет содержать группу участников, и выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-119">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="bc0cc-120">Использование модуля Microsoft Azure Active Directory для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc0cc-120">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="bc0cc-121">Сначала [подключитесь к клиенту Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="bc0cc-121">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="bc0cc-122">Добавление и удаление учетных записей пользователей в качестве участников группы</span><span class="sxs-lookup"><span data-stu-id="bc0cc-122">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="bc0cc-123">**Чтобы добавить учетную запись пользователя по имени участника**-пользователя, заполните имя участника-пользователя для учетной записи пользователя (например: belindan@contoso.com) и отображаемое имя группы, удалите символы "<" и ">", а затем выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-123">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="bc0cc-124">**Чтобы добавить учетную запись пользователя по отображаемому имени**, заполните отображаемое имя учетной записи пользователя (например, Светланы Коноваловой) и отображаемое имя группы, а затем выполните указанные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-124">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="bc0cc-125">**Чтобы удалить учетную запись пользователя по имени участника**-пользователя, введите имя участника-пользователя (например: belindan@contoso.com) и отображаемое имя группы, а затем выполните приведенные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-125">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="bc0cc-126">**Чтобы удалить учетную запись пользователя по отображаемому имени**, заполните отображаемое имя учетной записи пользователя (например, Светланы Коноваловой) и отображаемое имя группы, а затем выполните указанные ниже команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-126">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="bc0cc-127">Добавление и удаление групп в качестве участников группы</span><span class="sxs-lookup"><span data-stu-id="bc0cc-127">Add or remove groups as members of a group</span></span>

<span data-ttu-id="bc0cc-128">Группы безопасности могут содержать другие группы в качестве участников.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-128">Security groups can contain other groups as members.</span></span> <span data-ttu-id="bc0cc-129">Однако группы Microsoft 365 не могут.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-129">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="bc0cc-130">В этом разделе содержатся команды PowerShell для добавления или удаления групп только для группы безопасности.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-130">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="bc0cc-131">**Чтобы добавить группу по отображаемому имени**, укажите отображаемое имя добавляемой группы и отображаемое имя группы, которая будет содержать группу участников, и выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-131">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="bc0cc-132">**Чтобы удалить группу по отображаемому имени**, укажите отображаемое имя группы, которую нужно удалить, и отображаемое имя группы, которая будет содержать группу участников, и выполните следующие команды в окне PowerShell или в интегрированной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-132">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="bc0cc-133">См. также</span><span class="sxs-lookup"><span data-stu-id="bc0cc-133">See also</span></span>

[<span data-ttu-id="bc0cc-134">Управление учетными записями пользователей, лицензиями и группами Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc0cc-134">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="bc0cc-135">Управление Microsoft 365 с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc0cc-135">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="bc0cc-136">Начало работы с PowerShell для Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bc0cc-136">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

