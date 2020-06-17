---
title: Назначение лицензий Microsoft 365 учетным записям пользователей
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: В этой статье описано, как назначать лицензии на Microsoft 365 для учетных записей пользователей по отдельности или в зависимости от принадлежности к группе.
ms.openlocfilehash: f28b9a6367cec2f67b664db2d43ba55b9cf19638
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735937"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a><span data-ttu-id="71915-103">Назначение лицензий Microsoft 365 учетным записям пользователей</span><span class="sxs-lookup"><span data-stu-id="71915-103">Assign Microsoft 365 licenses to user accounts</span></span>

<span data-ttu-id="71915-104">*Эта статья относится как к Microsoft 365 Enterprise, так и к Office 365 корпоративный.*</span><span class="sxs-lookup"><span data-stu-id="71915-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="71915-105">Для модели удостоверения, которая используется только в облаке, вы можете назначить лицензии Microsoft 365 для учетных записей пользователей при их создании, в зависимости от того, как они создаются.</span><span class="sxs-lookup"><span data-stu-id="71915-105">For the cloud-only identity model, you can assign Microsoft 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="71915-106">Для модели гибридной идентификации при первой синхронизации учетных записей пользователей доменных служб Active Directory (AD DS) они не назначаются автоматически лицензии Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="71915-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned a Microsoft 365 license.</span></span> <span data-ttu-id="71915-107">Сначала необходимо настроить для каждой учетной записи пользователя расположение пользователя.</span><span class="sxs-lookup"><span data-stu-id="71915-107">You must first configure each user account with a user location.</span></span>

<span data-ttu-id="71915-108">В любом случае необходимо назначить лицензии учетным записям пользователей, чтобы пользователи могли получить доступ к службам Microsoft 365, таким как электронная почта и Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="71915-108">In either case, you must assign a license to user accounts so your users can access Microsoft 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="71915-109">Вы можете назначать лицензии учетным записям пользователей по отдельности или автоматически с помощью членства в группе.</span><span class="sxs-lookup"><span data-stu-id="71915-109">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="71915-110">Чтобы назначить лицензии Microsoft 365 отдельным учетным записям пользователей, можно использовать:</span><span class="sxs-lookup"><span data-stu-id="71915-110">To assign Microsoft 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="71915-111">Центр администрирования Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="71915-111">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [<span data-ttu-id="71915-112">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="71915-112">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="71915-113">Для автоматического назначения лицензий просмотрите раздел [Лицензирование на основе групп в Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="71915-113">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="71915-114">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="71915-114">Next steps</span></span>

<span data-ttu-id="71915-115">С полным набором учетных записей пользователей, которым были назначены лицензии, вы можете:</span><span class="sxs-lookup"><span data-stu-id="71915-115">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="71915-116">Реализация безопасности</span><span class="sxs-lookup"><span data-stu-id="71915-116">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="71915-117">Развертывание клиентского программного обеспечения, например Microsoft 365 Apps</span><span class="sxs-lookup"><span data-stu-id="71915-117">Deploy client software, such as Microsoft 365 Apps</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [<span data-ttu-id="71915-118">Настройка управления мобильными устройствами в Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="71915-118">Set up Mobile Device Management in Microsoft 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="71915-119">Настройка служб и приложений</span><span class="sxs-lookup"><span data-stu-id="71915-119">Configure services and applications</span></span>](configure-services-and-applications.md)
