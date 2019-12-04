---
title: Удостоверения для Office 365 в облаке
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: В этой статье описано, как создавать пользователей и группы, когда ваша подписка на Office 365 использует удостоверения, предназначенные только для облака.
ms.openlocfilehash: 6815c89821216416379a27eb525e66b90b828ea8
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813417"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="24796-103">Удостоверения для Office 365 в облаке</span><span class="sxs-lookup"><span data-stu-id="24796-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="24796-104">*Эта статья относится к Office 365 корпоративный и Microsoft 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="24796-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="24796-105">При использовании удостоверения только в облаке все пользователи, группы и контакты хранятся в клиенте Azure Active Directory (Azure AD) вашей подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="24796-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="24796-106">Ниже приведены основные компоненты удостоверения "только облако".</span><span class="sxs-lookup"><span data-stu-id="24796-106">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="24796-107">Пользователи и их учетные записи в организациях могут быть разбиты на несколько способов.</span><span class="sxs-lookup"><span data-stu-id="24796-107">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="24796-108">Например, некоторые из них имеют статус постоянных сотрудников.</span><span class="sxs-lookup"><span data-stu-id="24796-108">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="24796-109">Некоторые являются поставщиками, подрядчиками или партнерами с временным статусом.</span><span class="sxs-lookup"><span data-stu-id="24796-109">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="24796-110">Кроме того, существуют внешние пользователи, у которых нет учетных записей, но которым все равно необходимо предоставить доступ к определенным службам и ресурсам в целях взаимодействия и совместной работы.</span><span class="sxs-lookup"><span data-stu-id="24796-110">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="24796-111">Например:</span><span class="sxs-lookup"><span data-stu-id="24796-111">For example:</span></span>

- <span data-ttu-id="24796-112">учетные записи клиента представляют пользователей в вашей организации, которым вы предоставляете лицензии на доступ к облачным службам;</span><span class="sxs-lookup"><span data-stu-id="24796-112">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="24796-113">Учетные записи "бизнес-бизнес" (B2B) представляют пользователей за пределами вашей организации, которые приглашают принять участие в совместной работе.</span><span class="sxs-lookup"><span data-stu-id="24796-113">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="24796-114">Как они группируются?</span><span class="sxs-lookup"><span data-stu-id="24796-114">What are the groupings?</span></span> <span data-ttu-id="24796-115">Например, вы можете группировать пользователей по ролям высокого уровня или обязанностям в организации.</span><span class="sxs-lookup"><span data-stu-id="24796-115">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="24796-116">Кроме того, доступ к некоторым облачным службам можно предоставлять пользователям за пределами организации, у которых нет учетных записей.</span><span class="sxs-lookup"><span data-stu-id="24796-116">Additionally, some cloud services can be shared with users outside your organization without any user accounts.</span></span> <span data-ttu-id="24796-117">Вам потребуется определить и эти группы пользователей.</span><span class="sxs-lookup"><span data-stu-id="24796-117">You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="24796-118">Группы в Azure AD можно использовать для нескольких целей, и это упрощает управление облачной средой.</span><span class="sxs-lookup"><span data-stu-id="24796-118">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="24796-119">Например, с помощью групп Azure AD можно выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="24796-119">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="24796-120">Используйте Лицензирование на основе групп для автоматического назначения лицензий на Office 365 для учетных записей пользователей сразу после их добавления.</span><span class="sxs-lookup"><span data-stu-id="24796-120">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="24796-121">Динамически добавлять учетные записи пользователей в определенные группы на основании атрибутов этих учетных записей, например атрибута "Отдел".</span><span class="sxs-lookup"><span data-stu-id="24796-121">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="24796-122">Автоматически подготавливать пользователей для приложений класса "программное обеспечение как услуга" (SaaS) и защищать доступ к этим приложениям с помощью многофакторной проверки подлинности и других правил условного доступа.</span><span class="sxs-lookup"><span data-stu-id="24796-122">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="24796-123">Подготавливать разрешения и уровни доступа для сайтов групп SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="24796-123">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="24796-124">Вы можете создавать новых ***пользователей*** с помощью следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="24796-124">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="24796-125">Центр администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="24796-125">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="24796-126">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="24796-126">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="24796-127">Вы можете создавать новые ***группы*** с помощью следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="24796-127">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="24796-128">Центр администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="24796-128">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="24796-129">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="24796-129">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="24796-130">Следующий шаг для удостоверений только в облаке</span><span class="sxs-lookup"><span data-stu-id="24796-130">Next step for cloud-only identities</span></span>

[<span data-ttu-id="24796-131">Назначение лицензий учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="24796-131">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
